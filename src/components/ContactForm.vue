<template>
  <div class="contact-form-container">
    <h2 class="section-title mb-4">Get In Touch</h2>
    <p class="section-subtitle mb-5">Feel free to contact me for any opportunities or questions!</p>
    
    <form @submit.prevent="submitForm" class="contact-form">
      <!-- Name Field -->
      <div class="mb-4">
        <label for="name" class="form-label text-light">Your Name</label>
        <input 
          type="text" 
          class="form-control bg-dark-light border-dark text-light" 
          id="name" 
          v-model="formData.name"
          required
          placeholder="Enter your name"
        />
      </div>

      <!-- Email Field -->
      <div class="mb-4">
        <label for="email" class="form-label text-light">Your Email</label>
        <input 
          type="email" 
          class="form-control bg-dark-light border-dark text-light" 
          id="email" 
          v-model="formData.email"
          required
          placeholder="Enter your email"
        />
      </div>

      <!-- Message Field -->
      <div class="mb-4">
        <label for="message" class="form-label text-light">Your Message</label>
        <textarea 
          class="form-control bg-dark-light border-dark text-light" 
          id="message" 
          rows="5"
          v-model="formData.message"
          required
          placeholder="Enter your message"
        ></textarea>
      </div>

      <!-- reCAPTCHA Container -->
      <div class="mb-4">
        <div ref="recaptchaContainer" id="recaptcha-container"></div>
        <!-- Debug: Para makita kung nagre-render -->
        <p v-if="!recaptchaRendered" class="text-warning small text-center mt-2">
          <i class="fas fa-spinner fa-spin me-1"></i> Loading security verification...
        </p>
      </div>

      <!-- Submit Button -->
      <button 
        type="submit" 
        class="btn btn-primary btn-lg w-100"
        :disabled="isLoading"
      >
        <span v-if="isLoading" class="spinner-border spinner-border-sm me-2"></span>
        {{ isLoading ? 'Sending...' : 'Send Message' }}
      </button>
    </form>
  </div>
</template>

<script setup>
import { ref, reactive, onMounted, onBeforeUnmount, nextTick } from 'vue';
import { Notyf } from 'notyf';
import 'notyf/notyf.min.css';

// Web3Forms Configuration
const WEB3FORMS_ACCESS_KEY = "cba708f6-f732-4704-9dd3-4a794110fec8";

// ✅ UPDATED: Correct Site Key
const SITE_KEY = "6Lclh0UtAAAAAAY9l9WYppWQPxDnq2piIN8Duhht";

// Form Data
const formData = reactive({
  name: "",
  email: "",
  message: ""
});

// State
const isLoading = ref(false);
const recaptchaContainer = ref(null);
const recaptchaWidgetId = ref(null);
const recaptchaToken = ref("");
const recaptchaRendered = ref(false);

// Notyf
const notyf = new Notyf({
  duration: 4000,
  position: {
    x: 'right',
    y: 'top'
  },
  types: [
    {
      type: 'success',
      background: '#10b981',
      icon: {
        className: 'fas fa-check-circle',
        tagName: 'i',
        text: ''
      }
    },
    {
      type: 'error',
      background: '#ef4444',
      icon: {
        className: 'fas fa-exclamation-circle',
        tagName: 'i',
        text: ''
      }
    }
  ]
});

// Callback called by reCAPTCHA when successful
const onRecaptchaSuccess = (token) => {
  console.log('✅ reCAPTCHA Success! Token:', token);
  recaptchaToken.value = token;
  recaptchaRendered.value = true;
};

// Callback when expired
const onRecaptchaExpired = () => {
  console.log('⏰ reCAPTCHA Expired');
  recaptchaToken.value = "";
  recaptchaRendered.value = false;
  resetRecaptcha();
};

// Function to render the reCAPTCHA widget
const renderRecaptcha = () => {
  console.log('🔄 Attempting to render reCAPTCHA...');
  console.log('Site Key:', SITE_KEY);
  
  if (!window.grecaptcha) {
    console.error('❌ reCAPTCHA not loaded - window.grecaptcha is undefined');
    return;
  }
  
  if (!recaptchaContainer.value) {
    console.error('❌ recaptchaContainer is null');
    return;
  }

  try {
    recaptchaWidgetId.value = window.grecaptcha.render(recaptchaContainer.value, {
      sitekey: SITE_KEY,
      size: 'normal',
      callback: onRecaptchaSuccess,
      'expired-callback': onRecaptchaExpired,
    });
    console.log('✅ reCAPTCHA rendered! Widget ID:', recaptchaWidgetId.value);
    recaptchaRendered.value = true;
  } catch (error) {
    console.error('❌ Error rendering reCAPTCHA:', error);
  }
};

// Function to reset reCAPTCHA
const resetRecaptcha = () => {
  if (recaptchaWidgetId.value !== null && window.grecaptcha) {
    window.grecaptcha.reset(recaptchaWidgetId.value);
    recaptchaToken.value = "";
    recaptchaRendered.value = false;
  }
};

// Check if reCAPTCHA is ready
const waitForRecaptcha = () => {
  return new Promise((resolve) => {
    let attempts = 0;
    const maxAttempts = 50; // 5 seconds max
    
    const check = setInterval(() => {
      attempts++;
      console.log(`⏳ Waiting for reCAPTCHA... Attempt ${attempts}`);
      
      if (window.grecaptcha && typeof window.grecaptcha.render === 'function') {
        clearInterval(check);
        console.log('✅ reCAPTCHA is ready!');
        resolve(true);
      } else if (attempts >= maxAttempts) {
        clearInterval(check);
        console.error('❌ reCAPTCHA timeout after 5 seconds');
        resolve(false);
      }
    }, 100);
  });
};

onMounted(async () => {
  console.log('🚀 Component mounted');
  console.log('Using Site Key:', SITE_KEY);
  
  // Wait for DOM to be fully rendered
  await nextTick();
  
  // Wait for reCAPTCHA to load
  const isReady = await waitForRecaptcha();
  
  if (isReady) {
    // Small delay to ensure DOM is ready
    setTimeout(() => {
      renderRecaptcha();
    }, 200);
  } else {
    notyf.error('Failed to load security verification. Please refresh the page.');
  }
});

onBeforeUnmount(() => {
  // Clean up if needed
  if (recaptchaWidgetId.value !== null && window.grecaptcha) {
    try {
      window.grecaptcha.reset(recaptchaWidgetId.value);
    } catch (e) {
      // Ignore
    }
  }
});

// Submit Form
const submitForm = async () => {
  console.log('📤 Submitting form...');
  console.log('recaptchaToken:', recaptchaToken.value);
  
  // Validate reCAPTCHA
  if (!recaptchaToken.value) {
    notyf.error('Please verify that you are not a robot');
    return;
  }

  // Validate form fields
  if (!formData.name || !formData.email || !formData.message) {
    notyf.error('Please fill in all fields');
    return;
  }

  isLoading.value = true;

  try {
    const response = await fetch("https://api.web3forms.com/submit", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Accept: "application/json",
      },
      body: JSON.stringify({
        access_key: WEB3FORMS_ACCESS_KEY,
        subject: "New Contact Form Submission - Portfolio",
        from_name: "Portfolio Website",
        name: formData.name,
        email: formData.email,
        message: formData.message,
        "g-recaptcha-response": recaptchaToken.value
      }),
    });

    const result = await response.json();
    console.log('📥 Response from server:', result);
    
    if (result.success) {
      // Reset form
      formData.name = "";
      formData.email = "";
      formData.message = "";
      
      // Reset reCAPTCHA
      resetRecaptcha();
      
      // Re-render reCAPTCHA
      setTimeout(() => {
        renderRecaptcha();
      }, 500);
      
      // Show success message
      notyf.success("Message sent successfully! I'll get back to you soon.");
    } else {
      notyf.error("Failed to send message. Please try again.");
    }
  } catch (error) {
    console.error("❌ Error submitting form:", error);
    notyf.error("An error occurred. Please try again later.");
  } finally {
    isLoading.value = false;
  }
};
</script>

<style scoped>
.contact-form-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 2rem;
  background-color: rgba(30, 41, 59, 0.8);
  border-radius: 10px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
}

.contact-form .form-control {
  background-color: #1e293b;
  border: 1px solid #334155;
  color: #f1f5f9;
  padding: 0.75rem;
  border-radius: 5px;
  transition: all 0.3s ease;
}

.contact-form .form-control:focus {
  border-color: #3b82f6;
  box-shadow: 0 0 0 0.25rem rgba(59, 130, 246, 0.25);
  background-color: #1e293b;
  color: #f1f5f9;
}

.contact-form .form-control::placeholder {
  color: #94a3b8;
}

.contact-form label {
  font-weight: 500;
  margin-bottom: 0.5rem;
  display: block;
}

.btn-primary {
  background: linear-gradient(45deg, #0d6efd, #6f42c1);
  border: none;
  padding: 0.75rem 1.5rem;
  font-weight: 500;
  transition: all 0.3s ease;
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(13, 110, 253, 0.4);
}

.btn-primary:disabled {
  opacity: 0.7;
  cursor: not-allowed;
  transform: none;
}

#recaptcha-container {
  display: flex;
  justify-content: center;
  margin: 1.5rem 0;
  min-height: 78px;
}

/* Dark mode adjustments for reCAPTCHA */
.g-recaptcha {
  transform: scale(0.85);
  transform-origin: 0 0;
}

@media (max-width: 768px) {
  .contact-form-container {
    padding: 1.5rem;
  }
  
  .g-recaptcha {
    transform: scale(0.8);
  }
}

.text-warning {
  color: #fbbf24;
  font-size: 0.875rem;
}

.text-center {
  text-align: center;
}

.mt-2 {
  margin-top: 0.5rem;
}

.me-1 {
  margin-right: 0.25rem;
}

.fa-spinner {
  animation: fa-spin 2s infinite linear;
}

@keyframes fa-spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>
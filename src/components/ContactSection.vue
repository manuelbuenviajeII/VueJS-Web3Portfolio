<template>
  <section id="contact" class="contact-section py-5">
    <div class="container">
      <div class="row">
        <div class="col-12 text-center mb-5">
          <h2 class="section-title">Contact Me</h2>
          <p class="section-subtitle">Get in touch for collaborations or inquiries</p>
        </div>
      </div>

      <!-- Map Section -->
      <div class="row mb-5">
        <div class="col-12">
          <div class="map-container">
            <iframe 
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d61371.807793682274!2d120.56077899999998!3d15.975053549999998!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x33913fb28b8acf8f%3A0x432ead83f669f54f!2sUrdaneta%20City%2C%20Pangasinan!5e0!3m2!1sen!2sph!4v1759240267199!5m2!1sen!2sph" 
              width="100%" 
              height="400" 
              style="border:0; border-radius: var(--border-radius);" 
              allowfullscreen="" 
              loading="lazy" 
              referrerpolicy="no-referrer-when-downgrade"
              class="map-iframe"
            ></iframe>
          </div>
        </div>
      </div>

      <div class="row">
        <!-- Contact Info -->
        <div class="col-lg-6 mb-4 mb-lg-0">
          <h3 class="mb-4">Let's Connect</h3>
          <p class="mb-4">I'm always open to discussing new opportunities, creative ideas, or partnerships to bring your vision to life.</p>
          
          <div class="contact-info mb-4">
            <div v-for="info in contactInfo" :key="info.label" class="d-flex align-items-center mb-3">
              <div class="contact-icon me-3">
                <i :class="info.icon"></i>
              </div>
              <div>
                <h5 class="mb-1">{{ info.label }}</h5>
                <p class="mb-0">{{ info.value }}</p>
              </div>
            </div>
          </div>
          
          <div class="social-links">
            <a v-for="social in socialLinks" :key="social.name" :href="social.url" class="social-link me-3" :title="social.title" target="_blank">
              <i :class="social.icon" class="fa-2x"></i>
            </a>
          </div>
        </div>
        
        <!-- Contact Form -->
        <div class="col-lg-6">
          <div class="contact-form-container p-4 rounded">
            <h4 class="mb-4">Send Me a Message</h4>
            <form @submit.prevent="handleSubmit">
              <div class="mb-3">
                <label for="name" class="form-label">Your Full Name</label>
                <input type="text" class="form-control" id="name" v-model="form.name" placeholder="Enter your full name" required>
              </div>
              <div class="mb-3">
                <label for="email" class="form-label">Your Email Address</label>
                <input type="email" class="form-control" id="email" v-model="form.email" placeholder="Enter your email address" required>
              </div>
              <div class="mb-3">
                <label for="subject" class="form-label">Message Subject</label>
                <input type="text" class="form-control" id="subject" v-model="form.subject" placeholder="What is this regarding?" required>
              </div>
              <div class="mb-3">
                <label for="message" class="form-label">Your Message</label>
                <textarea class="form-control" id="message" v-model="form.message" rows="5" placeholder="Tell me about your project or inquiry..." required></textarea>
              </div>
              
              <div ref="recaptchaContainer" class="recaptcha-wrapper"></div>
              
              <button type="submit" class="btn btn-primary btn-lg w-100" :disabled="isLoading">
                {{ isLoading ? 'Sending...' : 'Send Message' }}
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive, onMounted, onBeforeUnmount } from "vue";
import { Notyf } from 'notyf';
import 'notyf/notyf.min.css';

// --- CONFIGURATION ---
const WEB3FORMS_ACCESS_KEY = "bb3ae0fb-75b0-4e85-bb10-d461bf7a2337";
const SITE_KEY = '6Lc2ekotAAAAAMRA0qcmZzrgkwo9yhYnaN5mKr2d';

// --- REACTIVE STATE ---
const isLoading = ref(false);
const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
});

// Static data
const contactInfo = [
  { label: 'Location', value: 'Urdaneta Pangasinan, Philippines', icon: 'fas fa-map-marker-alt' },
  { label: 'Email', value: 'manuel.buenviajeii@gmail.com', icon: 'fas fa-envelope' },
  { label: 'Phone', value: '+(639) 91-260-8220', icon: 'fas fa-phone' }
];

const socialLinks = [
  { name: 'GitHub', title: 'GitHub Profile', url: 'https://github.com/manuelbuenviajeII', icon: 'fab fa-github' },
  { name: 'LinkedIn', title: 'LinkedIn Profile', url: 'https://www.linkedin.com/in/manuel-buenviaje-301a8b222/', icon: 'fab fa-linkedin' },
  { name: 'Twitter', title: 'Twitter Profile', url: 'https://twitter.com/manuelbuenviaje', icon: 'fab fa-twitter' },
  { name: 'Instagram', title: 'Instagram Profile', url: 'https://www.instagram.com/', icon: 'fab fa-instagram' }
];

const notyf = new Notyf();

// --- RECAPTCHA ---
const recaptchaContainer = ref(null);
const recaptchaWidgetId = ref(null);
const recaptchaToken = ref('');

function onRecaptchaSuccess(token) {
  recaptchaToken.value = token;
}

function onRecaptchaExpired() {
  recaptchaToken.value = '';
}

function renderRecaptcha() {
  if (!window.grecaptcha) {
    console.warn('reCAPTCHA not loaded yet');
    return;
  }
  recaptchaWidgetId.value = window.grecaptcha.render(recaptchaContainer.value, {
    sitekey: SITE_KEY,
    size: 'normal',
    callback: onRecaptchaSuccess,
    'expired-callback': onRecaptchaExpired,
  });
}

function resetRecaptcha() {
  if (recaptchaWidgetId.value !== null && window.grecaptcha) {
    window.grecaptcha.reset(recaptchaWidgetId.value);
    recaptchaToken.value = '';
  }
}

onMounted(() => {
  const interval = setInterval(() => {
    if (window.grecaptcha && window.grecaptcha.render) {
      renderRecaptcha();
      clearInterval(interval);
    }
  }, 100);

  onBeforeUnmount(() => {
    clearInterval(interval);
  });
});

// --- MAIN SUBMIT FUNCTION (ITO NA ANG HANDLER) ---
const handleSubmit = async () => {
  // 1. Check ReCAPTCHA
  // if(!recaptchaToken.value){
  // notyf.error('Please verify that you are not a robot');
  // return;
  // }

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
        name: form.name,
        email: form.email,
        subject: form.subject, 
        message: form.message,
      }),
    });

    const result = await response.json();

    if (result.success) {
      notyf.success("Message Sent! 🎉");
      
      // Reset form
      form.name = '';
      form.email = '';
      form.subject = '';
      form.message = '';
      resetRecaptcha();
    } else {
      notyf.error(result.message || "Failed to send message. Please try again.");
    }
  } 
  catch (error) {
    console.error("Fetch Error:", error);
    notyf.error("Network error. Please check your internet connection.");
  } 
  finally {
    isLoading.value = false;
  }
};
</script>

<style scoped>
/* Copy your existing CSS here */
.contact-section { background-color: var(--white); padding: var(--section-padding); }
.map-container { width: 100%; border-radius: var(--border-radius); overflow: hidden; box-shadow: var(--shadow-medium); }
.map-iframe { display: block; width: 100%; height: 400px; }
.contact-icon { width: 50px; height: 50px; background-color: var(--light-color); color: var(--primary-color); border-radius: 50%; display: flex; align-items: center; justify-content: center; flex-shrink: 0; transition: all 0.3s ease; }
.contact-icon:hover { background-color: var(--primary-color); color: var(--white); transform: scale(1.1); }
.contact-info .d-flex { margin-bottom: 1.5rem; }
.contact-form-container { background-color: var(--light-color); box-shadow: var(--shadow-light); border-radius: var(--border-radius); padding: 2rem; transition: box-shadow 0.3s ease; }
.contact-form-container:hover { box-shadow: var(--shadow-medium); }
.social-links { display: flex; gap: 1rem; margin-top: 1.5rem; }
.social-link { color: var(--text-color); transition: color 0.3s ease, transform 0.3s ease; display: inline-block; }
.social-link:hover { color: var(--primary-color); transform: translateY(-5px) scale(1.1); }
.recaptcha-wrapper { margin-bottom: 1rem; display: flex; justify-content: center; min-height: 78px; }
.btn:disabled { opacity: 0.7; cursor: not-allowed; }
@media (max-width: 992px) { .contact-info { margin-bottom: 2rem; } .social-links { justify-content: center; } .map-iframe { height: 350px; } }
@media (max-width: 768px) { .contact-section iframe { height: 300px; } .contact-form-container { padding: 1.5rem; } }
@media (max-width: 576px) { .contact-section { padding: 3rem 0; } .map-iframe { height: 250px; } .contact-form-container { padding: 1.2rem; } .social-links { flex-wrap: wrap; justify-content: center; } .contact-icon { width: 40px; height: 40px; } .contact-icon i { font-size: 1rem; } }
.form-control { border: 1px solid var(--dark-gray); border-radius: var(--border-radius); transition: border-color 0.3s ease, box-shadow 0.3s ease; padding: 0.75rem 1rem; }
.form-control:focus { border-color: var(--primary-color); box-shadow: 0 0 0 0.2rem rgba(108, 99, 255, 0.25); }
.form-label { font-weight: 600; color: var(--dark-color); }
</style>
<template>
  <section id="about-me" class="about-section py-5">
    <div class="container">
      <div class="row">
        <div class="col-12 text-center mb-5">
          <h2 class="section-title">About Me</h2>
          <p class="section-subtitle">Get to know more about my background and journey</p>
        </div>
      </div>
      <div class="row align-items-center">
        <div class="col-lg-6 mb-4 mb-lg-0">
          <div class="about-image">
            <img 
              src="https://scontent.fmnl35-1.fna.fbcdn.net/v/t39.30808-6/483526654_24155512354038892_4957505010177271580_n.jpg?stp=dst-jpg_tt6&cstp=mx960x953&ctp=s960x953&_nc_cat=106&_nc_map=urlgen_bucketless&ccb=1-7&_nc_sid=a5f93a&_nc_eui2=AeHrqrkF_XykLble-Ep8lTKtR-_5807YLatH7_nzTtgtq65xIKQtI0c7r61mnFbXBsFMDDLBIKTPcgoUTauEs4OJ&_nc_ohc=RBA3m3T3tOYQ7kNvwGF0GUU&_nc_oc=AdphoQT8k66QzODK-b9y_2gi1M0amQQ7vyVVCQ6JYodpYP3bswh8d8CDBJPv2L-PG_0&_nc_zt=23&_nc_ht=scontent.fmnl35-1.fna&_nc_gid=0mWmFxFzb67SQNctTGZHCw&_nc_ss=7b2a8&oh=00_AQNwDcJP3Sxuisp8Os_D_Kzcl5g2fJ8bi1XfaeF3rmxHqQ&oe=6AC2275F" 
              alt="Manuel Buenviaje II - Professional Headshot" 
              class="img-fluid rounded"
            >
          </div>
        </div>
        <div class="col-lg-6">
          <h3 class="mb-4">My Journey in Web Development</h3>
          <p class="mb-4">My career has been a journey of continuous growth, each step driven by a desire to learn and adapt. My foundation was built on the front lines as a security guard, where vigilance and integrity became second nature.</p>
          <p class="mb-4">Eager for a new challenge, I entered the dynamic world of BPO, sharpening my communication and problem-solving skills in a high-volume setting. This led me to the remote work landscape as a Virtual Assistant, where I became proficient in digital organization, time management, and leveraging technology to efficiently support clients.</p>
          <p class="mb-5">Throughout this journey, my fascination with how technology works—not just how to use it—continued to grow. This curiosity has culminated in my pursuit of web development, where I am now excited to transition from using digital tools to creating them, blending my rich background in client service with a newfound passion for coding.</p>
          
          <div class="row text-center">
            <div v-for="stat in stats" :key="stat.label" class="col-md-4 mb-3">
              <div class="stat-card p-3 rounded">
                <h4 class="fw-bold text-primary">{{ stat.value }}</h4>
                <p class="mb-0">{{ stat.label }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'About',
  data() {
    return {
      stats: [
        { value: '8+', label: 'Projects Completed' },
        { value: '2+', label: 'Years Experience' },
        { value: '5+', label: 'Happy Clients' }
      ]
    }
  }
}
</script>

<style scoped>
.about-section {
    background-color: var(--light-color);
    padding: var(--section-padding);
}

.about-image {
    padding: 1rem;
}

.about-image img {
    width: 100%;
    height: auto;
    box-shadow: var(--shadow-medium);
    transition: transform 0.3s ease;
    border-radius: 15px;
}

.about-image img:hover {
    transform: scale(1.02);
}

.stat-card {
    background-color: var(--white);
    box-shadow: var(--shadow-light);
    transition: transform 0.3s ease;
    border-radius: var(--border-radius);
    text-align: center;
}

.stat-card:hover {
    transform: translateY(-5px);
}

@media (max-width: 992px) {
    .about-image {
        margin-bottom: 2rem;
    }
}

@media (max-width: 768px) {
    .stat-card {
        margin-bottom: 1rem;
    }
}

@media (max-width: 576px) {
    .about-section {
        padding: 3rem 0;
    }
}
</style>

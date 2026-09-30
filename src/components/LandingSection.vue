<template>
  <section id="landing" class="landing-section">
    <div class="landing-overlay"></div>
    <div class="container">
      <div class="row align-items-center min-vh-100">
        <!-- Profile Image - Left side -->
        <div class="col-lg-6 text-center mb-4 mb-lg-0 order-1">
          <div class="profile-image-container">
            <img 
              src="https://scontent.fmnl35-1.fna.fbcdn.net/v/t1.6435-9/31902046_2194411433908966_5421820797251485696_n.jpg?stp=dst-jpg_tt6&cstp=mx719x728&ctp=s719x728&_nc_cat=100&_nc_map=urlgen_bucketless&ccb=1-7&_nc_sid=a5f93a&_nc_eui2=AeGF8YHEl_h4cyh7v8aUNE4cw4ghUExM-HrDiCFQTEz4erxrL6QceXlnatE5aNvJRhS1sdIwZhQg1qJitVy9EG-a&_nc_ohc=UqbGPB8dJbgQ7kNvwFOa6Lg&_nc_oc=AdoBk8XqrpyezzPLny8KMQ7y-GWVk689YjcFKxZEaG-bP8dhtPdmrFnJ-Jv-hJqTSiQ&_nc_zt=23&_nc_ht=scontent.fmnl35-1.fna&_nc_gid=i9QGZw4Bs5jSQN3G1D8QAA&_nc_ss=7b2a8&oh=00_AQMEUwm0zNDxFq7Q-4nnLfbanlZP4hbcdrNuPczlgBCgiQ&oe=6AE3EDE5" 
              alt="Manuel Buenviaje II - Web Developer" 
              class="profile-image"
            >
          </div>
        </div>
        <!-- Text Content - Right side -->
        <div class="col-lg-6 order-2">
          <h1 class="display-4 fw-bold mb-4">
            Hi, I'm <span style="color: var(--primary-color);">Manuel Buenviaje II</span>
          </h1>
          <h2 class="h3 mb-4" style="color: var(--white);">Full Stack Web Developer</h2>
          <p class="lead mb-5" style="color: rgba(255,255,255,0.9);">
            I create modern, responsive websites and applications that deliver exceptional user experiences across all devices. With a background in client service and a passion for technology, I bridge the gap between user needs and technical solutions.
          </p>
          <div class="d-flex flex-wrap gap-3">
            <a href="#projects" class="btn btn-primary btn-lg">View My Work</a>
            <a href="#contact" class="btn btn-outline-light btn-lg">Contact Me</a>
            <a 
              href="https://drive.google.com/file/d/1L_u0NnTaYCmrA1iXnZofTJdPgttva4tK/view?usp=sharing" 
              target="_blank" 
              class="btn btn-outline-light btn-lg"
            >
              <i class="fas fa-file-pdf me-2"></i>View Resume
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'LandingSection'
}
</script>

<style scoped>
.landing-section {
    background: #000000;
    color: var(--white);
    padding-top: 80px;
    min-height: 100vh;
    display: flex;
    align-items: center;
    position: relative;
}

.landing-overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 1;
}

.landing-section .container {
    position: relative;
    z-index: 2;
}

.profile-image-container {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1rem;
}

.profile-image {
    width: 100%;
    max-width: 350px;
    height: auto;
    aspect-ratio: 1;
    border-radius: 50%;
    object-fit: cover;
    border: 8px solid rgba(255, 255, 255, 0.2);
    box-shadow: var(--shadow-heavy);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.profile-image:hover {
    transform: scale(1.05);
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.3);
}

/* Responsive - On smaller screens, image goes on top */
@media (max-width: 992px) {
    .landing-section {
        text-align: center;
        padding: 120px 0 60px;
    }
    .landing-section .display-4 {
        font-size: 2.5rem;
    }
    .profile-image {
        max-width: 280px;
    }
    /* On mobile, image goes on top */
    .order-1 {
        order: 1 !important;
    }
    .order-2 {
        order: 2 !important;
    }
}

@media (max-width: 768px) {
    .landing-section .display-4 {
        font-size: 2rem;
    }
    .landing-section h2 {
        font-size: 1.5rem;
    }
    .landing-section p.lead {
        font-size: 1.1rem;
    }
    .profile-image {
        max-width: 250px;
    }
}

@media (max-width: 576px) {
    .landing-section {
        padding: 100px 0 40px;
    }
    .landing-section .display-4 {
        font-size: 1.75rem;
    }
    .landing-section h2 {
        font-size: 1.25rem;
    }
    .landing-section p.lead {
        font-size: 1rem;
    }
    .landing-section .d-flex {
        flex-direction: column;
        gap: 1rem;
    }
    .landing-section .btn {
        width: 100%;
        max-width: 250px;
        margin: 0 auto;
    }
    .profile-image {
        max-width: 200px;
    }
}

@media (max-width: 400px) {
    .profile-image {
        max-width: 180px;
    }
    .landing-section .display-4 {
        font-size: 1.5rem;
    }
}

@media (max-height: 700px) and (max-width: 768px) {
    .landing-section {
        min-height: auto;
        padding: 120px 0 60px;
    }
}
</style>

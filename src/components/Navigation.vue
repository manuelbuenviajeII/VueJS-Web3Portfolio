<template>
  <nav class="navbar navbar-expand-lg fixed-top custom-navbar">
    <div class="container">
      <a class="navbar-brand" href="#">PORTFOLIO</a>
      <button 
        class="navbar-toggler" 
        type="button" 
        data-bs-toggle="collapse" 
        data-bs-target="#navbarNav"
        aria-controls="navbarNav" 
        aria-expanded="false" 
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <a class="nav-link" href="#landing">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#about-me">About Me</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#projects">Projects</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#tools">Tools</a>
          </li>
          <li class="nav-item">
            <a 
              class="nav-link resume-link" 
              href="https://drive.google.com/file/d/1AzD5kad1Z_ddI57giBzt-1aJbG4BKZxx/view?usp=sharing" 
              target="_blank"
            >
              <i class="fas fa-file-pdf me-1"></i>Resume
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#contact">Contact</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Navigation'
}
</script>

<style scoped>
.custom-navbar {
    background-color: var(--white) !important;
    box-shadow: var(--shadow-light);
    transition: all 0.3s ease;
    padding: 1rem 0;
}

.navbar-brand {
    font-family: var(--heading-font);
    font-weight: 700;
    font-size: 1.5rem;
    color: var(--dark-color) !important;
}

.navbar-nav .nav-link {
    font-family: var(--body-font);
    font-weight: 500;
    color: var(--text-color) !important;
    margin: 0 0.5rem;
    transition: color 0.3s ease;
    position: relative;
}

.navbar-nav .nav-link:hover {
    color: var(--primary-color) !important;
}

.navbar-nav .nav-link::after {
    content: '';
    position: absolute;
    width: 0;
    height: 2px;
    background: var(--primary-color);
    bottom: 0;
    left: 0;
    transition: width 0.3s ease;
}

.navbar-nav .nav-link:hover::after {
    width: 100%;
}

.resume-link {
    color: var(--accent-color) !important;
    font-weight: 600 !important;
}

.resume-link:hover {
    color: var(--primary-color) !important;
}

/* Mobile menu */
@media (max-width: 992px) {
    .navbar-nav {
        text-align: center;
        padding: 1rem 0;
    }
    .navbar-nav .nav-item {
        margin: 0.5rem 0;
    }
    .resume-link {
        display: inline-block;
        margin-top: 0.5rem;
    }
}

/* Fix for navbar toggler icon color */
.navbar-toggler {
    border-color: var(--dark-color);
}

.navbar-toggler-icon {
    background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 30 30'%3e%3cpath stroke='rgba(45, 43, 85, 1)' stroke-linecap='round' stroke-miterlimit='10' stroke-width='2' d='M4 7h22M4 15h22M4 23h22'/%3e%3c/svg%3e");
}
</style>
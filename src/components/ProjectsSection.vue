<template>
  <section id="projects" class="projects-section py-5">
    <div class="container">
      <div class="row">
        <div class="col-12 text-center mb-5">
          <h2 class="section-title">My Projects</h2>
          <p class="section-subtitle">Some of my recent work showcasing my skills in web development</p>
        </div>
      </div>
      <div class="row">
        <div v-for="project in projects" :key="project.id" class="col-lg-4 col-md-6 mb-4">
          <div class="card project-card h-100">
            <div class="project-image" v-if="project.image">
              <img :src="project.image" class="card-img-top" :alt="project.title">
            </div>
            <div class="project-image placeholder-image" v-else>
              <div class="placeholder-content">
                <i class="fas fa-plus fa-3x text-muted"></i>
                <p class="mt-2">Your Next Project Here</p>
              </div>
            </div>
            <div class="card-body d-flex flex-column">
              <h5 class="card-title">{{ project.title }}</h5>
              <p class="card-text">{{ project.description }}</p>
              <div class="project-tech mb-3">
                <span v-for="tech in project.technologies" :key="tech" class="badge bg-light text-dark">
                  {{ tech }}
                </span>
              </div>
              <div class="mt-auto">
                <a v-if="project.liveLink" :href="project.liveLink" class="btn btn-primary me-2">
                  <i class="fas fa-external-link-alt me-1"></i> {{ project.liveLabel || 'Live Demo' }}
                </a>
                <a v-if="project.codeLink" :href="project.codeLink" class="btn btn-outline-primary">
                  <i class="fab fa-github me-1"></i> Source Code
                </a>
                <a v-else-if="project.contactLink" :href="project.contactLink" class="btn btn-outline-primary w-100">
                  Suggest a Project
                </a>
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
  name: 'Projects',
  data() {
    return {
      projects: [
        {
          id: 1,
          title: 'E-commerce API Documentation',
          description: 'Dynamic E-Commerce Workflow Management. The system features dynamic routes for order processing, real-time inventory updates, and secure user authentication.',
          image: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?ixlib=rb-4.0.3&auto=format&fit=crop&w=700&q=80',
          technologies: ['API', 'Swagger', 'OpenAPI', 'Markdown'],
          liveLink: '#',
          liveLabel: 'View Docs',
          codeLink: '#'
        },
        {
          id: 2,
          title: 'Course Booking API Documentation',
          description: 'RESTful API for managing course enrollments, featuring user registration, authentication, and retrieval of user details.',
          image: 'https://images.unsplash.com/photo-1516321318423-f06f85e504b3?ixlib=rb-4.0.3&auto=format&fit=crop&w=700&q=80',
          technologies: ['REST API', 'Postman', 'JSON', 'Documentation'],
          liveLink: '#',
          liveLabel: 'View Docs',
          codeLink: '#'
        },
        {
          id: 3,
          title: 'Course Booking Application',
          description: 'MREN-stack course enrollment system featuring user registration, authentication, and profile management.',
          image: 'https://images.unsplash.com/photo-1501504905252-473c47e087f8?ixlib=rb-4.0.3&auto=format&fit=crop&w=700&q=80',
          technologies: ['React', 'Node.js', 'MongoDB', 'Stripe API'],
          liveLink: '#',
          liveLabel: 'Live Demo',
          codeLink: '#'
        },
        {
          id: 4,
          title: 'E-commerce Application',
          description: 'MRN E-Commerce Platform features dynamic product catalog with filtering and sorting real-time search.',
          image: 'https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?ixlib=rb-4.0.3&auto=format&fit=crop&w=700&q=80',
          technologies: ['Vue.js', 'Express', 'MySQL', 'PayPal API'],
          liveLink: '#',
          liveLabel: 'Live Demo',
          codeLink: '#'
        },
        {
          id: 5,
          title: 'Airline Booking System Mockup',
          description: 'Side Project Conceptual design showcasing an intuitive UI for flight search, seat selection, and booking confirmation.',
          image: 'https://images.unsplash.com/photo-1436491865332-7a61a109cc05?ixlib=rb-4.0.3&auto=format&fit=crop&w=700&q=80',
          technologies: ['Figma', 'UI Design', 'Wireframing', 'Prototyping'],
          liveLink: '#',
          liveLabel: 'View Mockup',
          codeLink: '#',
          codeLabel: 'Design File'
        },
        {
          id: 6,
          title: 'Airline Booking System Prototype',
          description: 'Interactive prototype of an airline booking system with functional flight search, booking flow, and payment simulation.',
          image: 'https://images.unsplash.com/photo-1436491865332-7a61a109cc05?ixlib=rb-4.0.3&auto=format&fit=crop&w=700&q=80',
          technologies: ['Figma', 'Prototyping', 'User Testing', 'Interaction Design'],
          liveLink: '#',
          liveLabel: 'View Prototype',
          codeLink: '#',
          codeLabel: 'Design File'
        },
        {
          id: 7,
          title: 'Short Courses Capstone Project',
          description: 'Placeholder for your Short courses capstone.',
          image: 'https://images.unsplash.com/photo-1522202176988-66273c2fd55f?ixlib=rb-4.0.3&auto=format&fit=crop&w=700&q=80',
          technologies: ['HTML/CSS', 'JavaScript', 'Bootstrap', 'REST API'],
          liveLink: '#',
          liveLabel: 'Live Demo',
          codeLink: '#'
        },
        {
          id: 8,
          title: 'Future Project',
          description: 'This space is reserved for my next exciting project. Stay tuned for updates as I continue to expand my portfolio.',
          image: null,
          technologies: ['Coming Soon'],
          liveLink: null,
          codeLink: null,
          contactLink: '#contact'
        }
      ]
    }
  }
}
</script>

<style scoped>
.projects-section {
    background-color: var(--white);
    padding: var(--section-padding);
}

.project-card {
    border: none;
    box-shadow: var(--shadow-light);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    overflow: hidden;
    border-radius: var(--border-radius-lg);
    height: 100%;
}

.project-card:hover {
    transform: translateY(-10px);
    box-shadow: var(--shadow-heavy);
}

.project-image {
    height: 200px;
    overflow: hidden;
}

.project-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.5s ease;
}

.project-card:hover .project-image img {
    transform: scale(1.1);
}

.project-tech .badge {
    margin-right: 0.5rem;
    margin-bottom: 0.5rem;
    font-size: 0.75rem;
}

.placeholder-image {
    background-color: var(--gray);
    display: flex;
    align-items: center;
    justify-content: center;
    height: 200px;
}

.placeholder-content {
    text-align: center;
    color: var(--text-light);
}

@media (max-width: 768px) {
    .project-card {
        margin-bottom: 1.5rem;
    }
}

@media (max-width: 576px) {
    .projects-section {
        padding: 3rem 0;
    }
    .project-tech .badge {
        font-size: 0.7rem;
        margin-right: 0.25rem;
        margin-bottom: 0.25rem;
    }
}
</style>
<template>
  <section id="tools" class="tools-section py-5">
    <div class="container">
      <div class="row">
        <div class="col-12 text-center mb-5">
          <h2 class="section-title">Tools & Technologies</h2>
          <p class="section-subtitle">Technologies and tools I work with to bring ideas to life</p>
        </div>
      </div>
      
      <!-- Frontend Development -->
      <div class="row mb-5">
        <div class="col-12 text-center mb-4">
          <h3 class="h4">Frontend Development</h3>
          <p class="text-muted">Creating responsive and interactive user interfaces</p>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6 text-center mb-4">
          <div class="tool-item p-4 rounded">
            <div class="tool-icon html">
              <i class="fab fa-html5 fa-4x"></i>
            </div>
            <h5 class="mt-3">HTML5</h5>
            <p class="small text-muted">Semantic markup &amp; structure</p>
          </div>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6 text-center mb-4">
          <div class="tool-item p-4 rounded">
            <div class="tool-icon css">
              <i class="fab fa-css3-alt fa-4x"></i>
            </div>
            <h5 class="mt-3">CSS3</h5>
            <p class="small text-muted">Styling &amp; animations</p>
          </div>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6 text-center mb-4">
          <div class="tool-item p-4 rounded">
            <div class="tool-icon javascript">
              <i class="fab fa-js-square fa-4x"></i>
            </div>
            <h5 class="mt-3">JavaScript</h5>
            <p class="small text-muted">Interactive functionality</p>
          </div>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6 text-center mb-4">
          <div class="tool-item p-4 rounded">
            <div class="tool-icon react">
              <i class="fab fa-react fa-4x"></i>
            </div>
            <h5 class="mt-3">React</h5>
            <p class="small text-muted">Component-based UI</p>
          </div>
        </div>
      </div>
      
      <!-- Backend Development -->
      <div class="row mb-5">
        <div class="col-12 text-center mb-4">
          <h3 class="h4">Backend Development</h3>
          <p class="text-muted">Building robust server-side applications and APIs</p>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6 text-center mb-4">
          <div class="tool-item p-4 rounded">
            <div class="tool-icon nodejs">
              <i class="fab fa-node-js fa-4x"></i>
            </div>
            <h5 class="mt-3">Node.js</h5>
            <p class="small text-muted">Server-side JavaScript</p>
          </div>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6 text-center mb-4">
          <div class="tool-item p-4 rounded">
            <div class="tool-icon php">
              <i class="fab fa-php fa-4x"></i>
            </div>
            <h5 class="mt-3">PHP</h5>
            <p class="small text-muted">Web application development</p>
          </div>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6 text-center mb-4">
          <div class="tool-item p-4 rounded">
            <div class="tool-icon python">
              <i class="fab fa-python fa-4x"></i>
            </div>
            <h5 class="mt-3">Python</h5>
            <p class="small text-muted">Scripting &amp; automation</p>
          </div>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6 text-center mb-4">
          <div class="tool-item p-4 rounded">
            <div class="tool-icon mysql">
              <i class="fas fa-database fa-4x"></i>
            </div>
            <h5 class="mt-3">MySQL</h5>
            <p class="small text-muted">Database management</p>
          </div>
        </div>
      </div>
      
      <!-- Development Tools -->
      <div class="row">
        <div class="col-12 text-center mb-4">
          <h3 class="h4">Development Tools</h3>
          <p class="text-muted">Essential tools for efficient development workflow</p>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6 text-center mb-4">
          <div class="tool-item p-4 rounded">
            <div class="tool-icon git">
              <i class="fab fa-git-alt fa-4x"></i>
            </div>
            <h5 class="mt-3">Git</h5>
            <p class="small text-muted">Version control system</p>
          </div>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6 text-center mb-4">
          <div class="tool-item p-4 rounded">
            <div class="tool-icon bootstrap">
              <i class="fab fa-bootstrap fa-4x"></i>
            </div>
            <h5 class="mt-3">Bootstrap</h5>
            <p class="small text-muted">CSS framework</p>
          </div>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6 text-center mb-4">
          <div class="tool-item p-4 rounded">
            <div class="tool-icon figma">
              <i class="fab fa-figma fa-4x"></i>
            </div>
            <h5 class="mt-3">Figma</h5>
            <p class="small text-muted">UI/UX design tool</p>
          </div>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6 text-center mb-4">
          <div class="tool-item p-4 rounded">
            <div class="tool-icon npm">
              <i class="fab fa-npm fa-4x"></i>
            </div>
            <h5 class="mt-3">NPM</h5>
            <p class="small text-muted">Package management</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ToolsSection'
}
</script>

<style scoped>
.tools-section {
    background-color: var(--light-color);
    padding: var(--section-padding);
}

.tool-item {
    background-color: var(--white);
    box-shadow: var(--shadow-light);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    height: 100%;
    border-radius: var(--border-radius);
    padding: 1.5rem;
    cursor: default;
}

.tool-item:hover {
    transform: translateY(-8px);
    box-shadow: var(--shadow-heavy);
}

/* Tool Icons */
.tool-icon {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 80px;
    height: 80px;
    margin: 0 auto;
    border-radius: 50%;
    transition: all 0.3s ease;
}

.tool-icon i {
    font-size: 3.5rem;
    transition: all 0.3s ease;
}

/* Individual Icon Colors */
.tool-icon.html {
    background-color: #f8f9fa;
    color: #e34f26;
}

.tool-icon.html:hover {
    background-color: #e34f26;
    color: white;
    transform: scale(1.1);
}

.tool-icon.css {
    background-color: #f8f9fa;
    color: #1572b6;
}

.tool-icon.css:hover {
    background-color: #1572b6;
    color: white;
    transform: scale(1.1);
}

.tool-icon.javascript {
    background-color: #f8f9fa;
    color: #f7df1e;
}

.tool-icon.javascript:hover {
    background-color: #f7df1e;
    color: #000;
    transform: scale(1.1);
}

.tool-icon.react {
    background-color: #f8f9fa;
    color: #61dafb;
}

.tool-icon.react:hover {
    background-color: #61dafb;
    color: #000;
    transform: scale(1.1) rotate(20deg);
}

.tool-icon.nodejs {
    background-color: #f8f9fa;
    color: #339933;
}

.tool-icon.nodejs:hover {
    background-color: #339933;
    color: white;
    transform: scale(1.1);
}

.tool-icon.php {
    background-color: #f8f9fa;
    color: #777bb4;
}

.tool-icon.php:hover {
    background-color: #777bb4;
    color: white;
    transform: scale(1.1);
}

.tool-icon.python {
    background-color: #f8f9fa;
    color: #3776ab;
}

.tool-icon.python:hover {
    background-color: #3776ab;
    color: #ffd43b;
    transform: scale(1.1);
}

.tool-icon.mysql {
    background-color: #f8f9fa;
    color: #4479a1;
}

.tool-icon.mysql:hover {
    background-color: #4479a1;
    color: white;
    transform: scale(1.1);
}

.tool-icon.git {
    background-color: #f8f9fa;
    color: #f05032;
}

.tool-icon.git:hover {
    background-color: #f05032;
    color: white;
    transform: scale(1.1);
}

.tool-icon.bootstrap {
    background-color: #f8f9fa;
    color: #7952b3;
}

.tool-icon.bootstrap:hover {
    background-color: #7952b3;
    color: white;
    transform: scale(1.1);
}

.tool-icon.figma {
    background-color: #f8f9fa;
    color: #f24e1e;
}

.tool-icon.figma:hover {
    background-color: #f24e1e;
    color: white;
    transform: scale(1.1);
}

.tool-icon.npm {
    background-color: #f8f9fa;
    color: #cb3837;
}

.tool-icon.npm:hover {
    background-color: #cb3837;
    color: white;
    transform: scale(1.1);
}

/* Tool Item Text */
.tool-item h5 {
    font-family: var(--heading-font);
    font-weight: 600;
    margin-top: 0.75rem;
    margin-bottom: 0.25rem;
    color: var(--dark-color);
}

.tool-item .small {
    font-size: 0.85rem;
    color: var(--text-light) !important;
}

/* Responsive */
@media (max-width: 768px) {
    .tool-item {
        margin-bottom: 1rem;
    }
    .tool-icon {
        width: 70px;
        height: 70px;
    }
    .tool-icon i {
        font-size: 2.5rem;
    }
}

@media (max-width: 576px) {
    .tools-section {
        padding: 3rem 0;
    }
    .tool-icon {
        width: 60px;
        height: 60px;
    }
    .tool-icon i {
        font-size: 2rem;
    }
}
</style>
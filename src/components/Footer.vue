<template>
  <footer class="footer py-4">
    <div class="container">
      <div class="row">
        <div class="col-12 text-center">
          <p class="mb-2">&copy; 2025 Manuel Buenviaje II. All Rights Reserved.</p>
          <p class="mb-0">Designed with <i class="fas fa-heart text-danger"></i> by Manuel Buenviaje II</p>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'AppFooter'
}
</script>

<style scoped>
/* Footer CSS */
.footer {
  background-color: #1a237e; /* Dark blue - similar to the design */
  color: #ffffff;
  width: 100%;
  margin-top: auto;
  border-top: 2px solid #283593;
}

.footer p {
  margin: 0;
  font-size: 0.95rem;
  letter-spacing: 0.5px;
  font-weight: 300;
}

.footer .text-danger {
  color: #ff4d4d !important;
}

/* Optional: subtle hover effect */
.footer:hover {
  background-color: #151d6e;
  transition: background-color 0.3s ease;
}

/* Heart pulse animation */
.fa-heart {
  display: inline-block;
  animation: heartbeat 1.5s ease-in-out infinite;
}

@keyframes heartbeat {
  0% { transform: scale(1); }
  14% { transform: scale(1.3); }
  28% { transform: scale(1); }
  42% { transform: scale(1.3); }
  70% { transform: scale(1); }
  100% { transform: scale(1); }
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .footer p {
    font-size: 0.85rem;
  }
}
</style>
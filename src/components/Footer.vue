<template>
    <footer class="footer">
      <div class="footer-content">
        <div class="footer-logo">
          <h3>Ali Tolga Çakır</h3>
        </div>
        <div class="footer-socials">
          <a href="https://github.com/alitolga0" target="_blank" class="social-link">
            <i class="fab fa-github"></i>
          </a>
          <a href="https://www.linkedin.com/in/ali-tolga-çakir-4429b7257" target="_blank" class="social-link">
            <i class="fab fa-linkedin"></i>
          </a>
          <a href="mailto:cakiralitolga1@gmail.com" class="social-link">
            <i class="fas fa-envelope"></i>
          </a>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; {{ new Date().getFullYear() }} Ali Tolga Çakır - Tüm hakları saklıdır.</p>
      </div>
    </footer>
  </template>
  
  <script>
  export default {
    name: "myFooter",
  };
  </script>
  
  <style scoped>
.footer {
  background-color: var(--bg-secondary);
  color: var(--text-main);
  padding: 40px 0 20px;
  text-align: center;
  border-top: var(--border-glass);
  margin-top: auto;
}

.footer-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 20px;
}

.footer-logo h3 {
  font-size: 1.8rem;
  background: var(--accent-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin: 0;
  font-weight: 700;
}

.footer-socials {
  display: flex;
  gap: 20px;
}

.social-link {
  color: var(--text-muted);
  font-size: 1.8rem;
  transition: var(--transition);
  display: flex;
  align-items: center;
  justify-content: center;
  width: 48px;
  height: 48px;
  border-radius: var(--radius-full);
  background-color: rgba(255, 255, 255, 0.03);
  border: var(--border-glass);
}

.social-link:hover {
  color: var(--text-main);
  background: var(--accent-gradient);
  box-shadow: var(--shadow-glow);
  transform: translateY(-3px);
  border-color: transparent;
}

.footer-bottom {
  margin-top: 30px;
  padding-top: 20px;
  border-top: var(--border-glass);
  width: 80%;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.footer-bottom p {
  font-size: 0.9rem;
  color: var(--text-muted);
}
</style>
  
<template>
  <div class="page-wrapper">
    <myNavbar />
    
    <div class="contact-container">
      <div class="contact-header fade-in">
        <h2 class="page-title">İletişime Geçin</h2>
        <p class="page-subtitle">Projeleriniz ve işbirlikleri için mesaj bırakabilirsiniz.</p>
      </div>

      <div class="contact-form-card fade-in">
        <form @submit.prevent="handleSubmit" class="contact-form">
          <div class="input-group">
            <input type="text" id="name" v-model="name" required placeholder=" " />
            <label for="name">Adınız</label>
          </div>
          
          <div class="input-group">
            <input type="email" id="email" v-model="email" required placeholder=" " />
            <label for="email">E-Posta</label>
          </div>
          
          <div class="input-group textarea-group">
            <textarea id="message" v-model="message" required placeholder=" "></textarea>
            <label for="message">Mesajınız</label>
          </div>
          
          <button type="submit" class="submit-button" :class="{ 'submitted': submitted }">
            <span v-if="!submitted">Mesaj Gönder <i class="fas fa-paper-plane"></i></span>
            <span v-else>Gönderildi <i class="fas fa-check"></i></span>
          </button>
        </form>
        
        <div v-if="submitted" class="submission-confirmation fade-in">
          Teşekkürler! Mesajınız en kısa sürede değerlendirilecek.
        </div>
      </div>
    </div>

    <myFooter />
  </div>
</template>

<script>
import myNavbar from '../components/Navbar.vue';
import myFooter from '../components/Footer.vue';

export default {
  name: 'ContactPage',
  components: {
    myNavbar,
    myFooter,
  },
  data() {
    return {
      name: '',
      email: '',
      message: '',
      submitted: false,
    };
  },
  methods: {
    handleSubmit() {
      
      if (!window.Email) {
        console.error("SMTP.js yüklenmedi. Lütfen kontrol edin.");
        return;
      }

      window.Email.send({
        Host: "", 
        Username: "", 
        Password: "", 
        To: '', 
        From: "", 
        Subject: `Yeni mesaj - ${this.email}`, 
        Body: `Ad: ${this.name} <br/> E-posta: ${this.email} <br/> Mesaj: ${this.message}`,
        Port: "",
      })
      .then(
        message => {
          if (message === 'OK') {
            this.submitted = true; 
            this.resetForm(); 
          } else {
            alert("Mesaj gönderilirken bir hata oluştu: " + message);
          }
        }
      )
      .catch(error => {
        console.error("E-posta gönderimi sırasında bir hata oluştu:", error);
      });
    },
    resetForm() {
      this.name = '';
      this.email = '';
      this.message = '';
    },
  },
};
</script><style scoped>
.page-wrapper {
  background-color: var(--bg-primary);
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.contact-container {
  flex: 1;
  width: 100%;
  max-width: 800px;
  margin: 0 auto;
  padding: 120px 20px 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.contact-header {
  text-align: center;
  margin-bottom: 40px;
}

.page-title {
  font-size: 3rem;
  font-weight: 800;
  margin-bottom: 10px;
  color: var(--text-main);
  background: var(--accent-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.page-subtitle {
  font-size: 1.1rem;
  color: var(--text-muted);
}

.contact-form-card {
  width: 100%;
  background: var(--bg-secondary);
  border: var(--border-glass);
  border-radius: var(--radius-lg);
  padding: 50px 40px;
  box-shadow: var(--shadow-md);
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.input-group {
  position: relative;
}

.input-group input,
.input-group textarea {
  width: 100%;
  padding: 15px 20px;
  background-color: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: var(--radius-md);
  color: var(--text-main);
  font-size: 1rem;
  font-family: inherit;
  transition: var(--transition);
}

.input-group textarea {
  min-height: 150px;
  resize: vertical;
}

.input-group label {
  position: absolute;
  left: 20px;
  top: 15px;
  color: var(--text-muted);
  pointer-events: none;
  transition: var(--transition);
  font-size: 1rem;
  background-color: var(--bg-secondary);
  padding: 0 5px;
}

/* Floating label effect */
.input-group input:focus ~ label,
.input-group input:not(:placeholder-shown) ~ label,
.input-group textarea:focus ~ label,
.input-group textarea:not(:placeholder-shown) ~ label {
  top: -10px;
  left: 15px;
  font-size: 0.85rem;
  color: var(--accent-primary);
}

.input-group input:focus,
.input-group textarea:focus {
  outline: none;
  border-color: var(--accent-primary);
  background-color: rgba(56, 189, 248, 0.05);
  box-shadow: 0 0 0 4px rgba(56, 189, 248, 0.1);
}

.submit-button {
  padding: 16px 30px;
  background: var(--accent-gradient);
  color: #fff;
  border: none;
  border-radius: var(--radius-md);
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: var(--transition);
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
  margin-top: 10px;
}

.submit-button:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-glow);
}

.submit-button.submitted {
  background: #10b981; /* Success green */
  pointer-events: none;
}

.submission-confirmation {
  margin-top: 25px;
  padding: 15px;
  background-color: rgba(16, 185, 129, 0.1);
  color: #10b981;
  border: 1px solid rgba(16, 185, 129, 0.2);
  border-radius: var(--radius-md);
  text-align: center;
  font-weight: 500;
}

.fade-in {
  animation: fadeIn 0.6s ease-out forwards;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(15px); }
  to { opacity: 1; transform: translateY(0); }
}

@media (max-width: 600px) {
  .contact-form-card {
    padding: 30px 20px;
  }
  
  .page-title {
    font-size: 2.5rem;
  }
}
</style>

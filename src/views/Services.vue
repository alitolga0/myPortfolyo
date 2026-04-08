<template>
  <div class="page-wrapper">
    <myNavbar />

    <div class="services-container">
      <div class="header-section fade-in">
        <h1 class="page-title">Hizmetlerim</h1>
        <p class="page-subtitle">Sizin için sunduğum profesyonel dijital çözümler.</p>
      </div>
      
      <div class="services-grid">
        <div class="service-card slide-up" v-for="(service, index) in services" :key="index" :style="{ animationDelay: `${index * 0.15}s` }">
          <div class="service-image-wrapper">
            <img :src="service.image" :alt="service.title" class="service-image" />
            <div class="image-overlay"></div>
          </div>
          <div class="service-text">
            <h2>{{ service.title }}</h2>
            <p>{{ service.description }}</p>
            <button class="learn-more-btn">
              İncele <i class="fas fa-arrow-right"></i>
            </button>
          </div>
        </div>
      </div>
    </div>

    <myFooter/>
  </div>
</template>

<script>
import myNavbar from '../components/Navbar.vue';
import myFooter from '../components/Footer.vue';
export default {
  name: 'ServicesPage',
  components: {
    myNavbar,
    myFooter,
  },
  data() {
    return {
      services: [
        {
          title: 'Web Geliştirme',
          description: 'Modern ve duyarlı web siteleri tasarlıyor ve geliştiriyorum. HTML, CSS ve JavaScript kullanarak kullanıcı dostu arayüzler oluşturuyorum.',
          image: require('@/assets/hizmet1.jpg'), 
        },
        {
          title: 'Mobil Geliştirme',
          description: 'Android ve iOS platformları için kullanıcı dostu mobil uygulamalar geliştiriyorum. React Native ve Flutter ile çapraz platform çözümleri sunuyorum.',
          image: require('@/assets/hizmet2.png'),
        },
        {
          title: 'UX/UI Tasarım',
          description: 'Kullanıcı deneyimini ön planda tutarak etkili ve estetik arayüz tasarımları yapıyorum. Kullanıcı odaklı yaklaşımla projelerimi şekillendiriyorum.',
          image: require('@/assets/hizmet3.jpg'), 
        },
        {
          title: 'WordPress Geliştirme',
          description: 'WordPress tabanlı web siteleri oluşturuyor ve özelleştiriyorum. Temalar ve eklentilerle kullanıcı dostu çözümler sunuyorum.',
          image: require('@/assets/hizmet4.jpg'), 
        },
      ],
    };
  },
};
</script>

<style scoped>
.page-wrapper {
  background-color: var(--bg-primary);
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.services-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 100px 20px 60px;
  flex: 1;
}

.header-section {
  text-align: center;
  margin-bottom: 60px;
}

.page-title {
  font-size: 3rem; 
  color: var(--text-main);
  font-weight: 800;
  margin-bottom: 15px;
  background: var(--accent-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.page-subtitle {
  font-size: 1.2rem;
  color: var(--text-muted);
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 40px;
}

.service-card {
  background-color: var(--bg-secondary);
  border-radius: var(--radius-lg); 
  border: var(--border-glass);
  overflow: hidden; 
  transition: var(--transition);
  display: flex;
  flex-direction: column;
}

.service-card:hover {
  transform: translateY(-10px); 
  box-shadow: var(--shadow-md), var(--shadow-glow); 
  border-color: rgba(56, 189, 248, 0.4);
}

.service-image-wrapper {
  position: relative;
  width: 100%;
  height: 220px;
  overflow: hidden;
}

.service-image {
  width: 100%; 
  height: 100%;
  object-fit: cover; 
  transition: transform 0.6s ease;
}

.service-card:hover .service-image {
  transform: scale(1.1);
}

.image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, var(--bg-secondary) 0%, transparent 100%);
}

.service-text {
  padding: 30px;
  flex: 1;
  display: flex;
  flex-direction: column;
}

.service-text h2 {
  margin: 0 0 15px;
  color: var(--text-main); 
  font-size: 1.6rem;
  font-weight: 700; 
}

.service-text p {
  margin: 0 0 25px;
  color: var(--text-muted); 
  line-height: 1.6;
  flex: 1;
}

.learn-more-btn {
  background: transparent;
  color: var(--accent-primary);
  border: none;
  font-size: 1rem;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 10px;
  cursor: pointer;
  padding: 0;
  transition: var(--transition);
  align-self: flex-start;
}

.learn-more-btn i {
  transition: transform 0.3s ease;
}

.learn-more-btn:hover {
  color: var(--text-main);
}

.learn-more-btn:hover i {
  transform: translateX(5px);
}

/* Animations */
.fade-in {
  animation: fadeIn 0.8s ease-out forwards;
}

.slide-up {
  opacity: 0;
  animation: slideUp 0.6s ease-out forwards;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@media (max-width: 600px) {
  .page-title {
    font-size: 2.5rem;
  }
  
  .services-grid {
    grid-template-columns: 1fr;
    gap: 30px;
  }
}
</style>

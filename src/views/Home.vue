<template>
  <div class="page-wrapper">
    <myNavbar />
    
    <section class="hero-section">
      <div class="hero-overlay"></div>
      <div class="hero-content">
        <h1 class="bounce-in">Software Developer</h1>
        <h2 class="slide-up">Ali Tolga Çakir</h2>
      </div>
    </section>

    <div class="container">
      <section class="about-me fade-in">
        <h2 class="section-title">Hakkımda</h2>
        <p class="about-text">
          Merhaba! Ben Ali Tolga Çakir, yazılım geliştirme konusunda tutkulu bir geliştiriciyim.
          Modern web ve mobil uygulama geliştirme üzerine deneyimim var. 
          Projelerimde her zaman kullanıcı deneyimini öncelikli hedefim olarak görüyorum. Sürekli öğrenmeyi ve yenilikleri takip
          etmeyi seviyorum. Amacım, kullanıcıların hayatını kolaylaştıran ve ilham veren çözümler üretmek.
        </p>
      </section>

      <section class="featured-projects fade-in">
        <h2 class="section-title">Öne Çıkan Projeler</h2>
        <div class="project-grid">
          <a
            v-for="project in projects"
            :key="project.id"
            :href="project.link"
            target="_blank"
            class="project-card"
          >
            <div class="image-wrapper">
              <img :src="project.image" alt="Project Image" />
              <div class="project-overlay">
                <h3 class="project-title">{{ project.title }}</h3>
                <span class="project-link-icon"><i class="fas fa-external-link-alt"></i></span>
              </div>
            </div>
          </a>
        </div>
      </section>
   
      <section class="services fade-in">
        <h2 class="section-title">Uzmanlık Alanlarım</h2>
        <div class="services-grid">
          <div v-for="service in services" :key="service.id" class="service-card">
            <div class="icon-wrapper">
              <i :class="service.icon" class="service-icon"></i>
            </div>
            <h3>{{ service.name }}</h3>
            <p>{{ service.description }}</p>
          </div>
        </div>
      </section>

      <div class="languages-wrapper fade-in">
        <myLanguages/>
      </div>
    </div>

    <myFooter/>
  </div>
</template>

<script>
import myLanguages from '../components/Languages.vue';
import myNavbar from '../components/Navbar.vue';
import myFooter from '../components/Footer.vue';

export default {
  name: 'HomePage',
  components: {
    myNavbar,
    myFooter,
    myLanguages,
  },
  data() {
    return {
      projects: [
        { id: 1, title: 'ECommerce App', image: require('@/assets/proje3.jpg'), link: 'https://github.com/alitolga0/ECommerceApp' }, 
        { id: 2, title: 'Smart Pet App', image: require('@/assets/proje1.jpg'), link: 'https://github.com/HakanDogann1/SmartPetProject' },
        { id: 3, title: 'Air Quality Monitoring', image: require('@/assets/proje2.jpg'), link: 'https://github.com/alitolga0/AirqualityMonitoring' },
      ],
      services: [
        { id: 1, name: 'Web Geliştirme', icon: 'fas fa-code', description: 'Modern ve dinamik web siteleri geliştiriyorum.' },
        { id: 2, name: 'Mobil Uygulama Geliştirme', icon: 'fas fa-mobile-alt', description: 'Mobil platformlar için uygulamalar tasarlıyorum.' },
        { id: 3, name: 'UI/UX Tasarımı', icon: 'fas fa-paint-brush', description: 'Kullanıcı dostu ve şık arayüzler sunuyorum.' },
      ],
    };
  },
};
</script>

<style scoped>
.page-wrapper {
  background-color: var(--bg-primary);
  min-height: 100vh;
}

.hero-section {
  position: relative;
  height: 70vh;
  min-height: 500px;
  background-image: url('../assets/kapak.jpeg'); 
  background-size: cover;
  background-position: center; 
  background-attachment: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  overflow: hidden;
}

.hero-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(to bottom, rgba(15, 23, 42, 0.6), rgba(15, 23, 42, 0.95));
  z-index: 1;
}

.hero-content {
  position: relative;
  z-index: 2;
  padding: 0 20px;
}

.hero-content h1 {
  font-size: clamp(3rem, 5vw, 4.5rem);
  font-weight: 800;
  margin-bottom: 15px;
  color: var(--text-main);
  background: var(--accent-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hero-content h2 {
  font-size: clamp(1.5rem, 3vw, 2.5rem);
  color: var(--text-muted);
  font-weight: 500;
  letter-spacing: 2px;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 20px;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--text-main);
  margin-bottom: 40px;
  text-align: center;
  position: relative;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 4px;
  background: var(--accent-gradient);
  border-radius: var(--radius-full);
}

.about-me {
  background-color: var(--bg-secondary);
  padding: 50px 40px;
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-sm);
  margin-bottom: 80px;
  border: var(--border-glass);
}

.about-text {
  font-size: 1.25rem;
  color: var(--text-muted);
  line-height: 1.8;
  text-align: center;
  max-width: 800px;
  margin: 0 auto;
}

.featured-projects {
  margin-bottom: 80px;
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
}

.project-card {
  display: block;
  border-radius: var(--radius-lg);
  overflow: hidden;
  position: relative;
  background-color: var(--bg-secondary);
  border: var(--border-glass);
  box-shadow: var(--shadow-sm);
  transition: var(--transition);
}

.project-card:hover {
  transform: translateY(-10px);
  box-shadow: var(--shadow-md), var(--shadow-glow);
  border-color: rgba(56, 189, 248, 0.4);
}

.image-wrapper {
  position: relative;
  width: 100%;
  height: 250px;
  overflow: hidden;
}

.image-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.project-card:hover .image-wrapper img {
  transform: scale(1.1);
}

.project-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(15, 23, 42, 0.9) 0%, rgba(15, 23, 42, 0.2) 100%);
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  padding: 25px;
  opacity: 0.9;
  transition: var(--transition);
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.project-title {
  color: var(--text-main);
  font-size: 1.4rem;
  font-weight: 600;
  margin-bottom: 5px;
  transform: translateY(10px);
  transition: var(--transition);
}

.project-card:hover .project-title {
  transform: translateY(0);
}

.project-link-icon {
  position: absolute;
  top: 20px;
  right: 20px;
  color: var(--text-main);
  background: var(--accent-gradient);
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transform: scale(0.5);
  transition: var(--transition);
}

.project-card:hover .project-link-icon {
  opacity: 1;
  transform: scale(1);
}

.services {
  margin-bottom: 80px;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 30px;
}

.service-card {
  background-color: var(--bg-secondary);
  border-radius: var(--radius-lg);
  padding: 40px 30px;
  text-align: center;
  border: var(--border-glass);
  transition: var(--transition);
}

.service-card:hover {
  transform: translateY(-8px);
  box-shadow: var(--shadow-md), var(--shadow-glow);
  border-color: rgba(56, 189, 248, 0.5);
}

.icon-wrapper {
  width: 80px;
  height: 80px;
  background: rgba(56, 189, 248, 0.1);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 20px;
  transition: var(--transition);
}

.service-card:hover .icon-wrapper {
  background: var(--accent-gradient);
  transform: scale(1.1) rotate(5deg);
}

.service-icon {
  font-size: 32px;
  color: var(--accent-primary);
  transition: var(--transition);
}

.service-card:hover .service-icon {
  color: var(--text-main);
}

.service-card h3 {
  font-size: 1.4rem;
  color: var(--text-main);
  margin-bottom: 15px;
  font-weight: 600;
}

.service-card p {
  color: var(--text-muted);
  font-size: 1rem;
  line-height: 1.6;
}

.languages-wrapper {
  margin-bottom: 40px;
}

/* Animations */
@keyframes bounceIn {
  0% { opacity: 0; transform: scale(0.9); }
  60% { opacity: 1; transform: scale(1.02); }
  100% { transform: scale(1); }
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

.bounce-in {
  animation: bounceIn 1s cubic-bezier(0.2, 0.8, 0.2, 1) forwards;
}

.slide-up {
  animation: slideUp 0.8s ease-out forwards;
  animation-delay: 0.3s;
  opacity: 0;
}

.fade-in {
  animation: fadeIn 1s ease-out forwards;
}

@media (max-width: 768px) {
  .hero-section {
    height: 50vh;
  }
  
  .about-me {
    padding: 30px 20px;
  }
  
  .section-title {
    font-size: 2rem;
  }
}
</style>

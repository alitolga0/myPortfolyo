<template>
  <div class="page-wrapper">
    <div class="nav-container">
      <myNavbar />
    </div>
    
    <div class="content-container">
      <button class="toggle-button" @click="toggleSidebar">
        <i :class="isSidebarVisible ? 'fas fa-times' : 'fas fa-bars'"></i>
      </button>
      
      <div class="sidebar-wrapper" :class="{ open: isSidebarVisible }">
        <ul class="sidebar-menu">
          <li @click="selectSection('about')" :class="{ active: selectedSection === 'about' }">
            <i class="fas fa-user-astronaut"></i> <span>Hakkımda</span>
          </li>
          <li @click="selectSection('education')" :class="{ active: selectedSection === 'education' }">
            <i class="fas fa-graduation-cap"></i> <span>Eğitimim</span>
          </li>
          <li @click="selectSection('experience')" :class="{ active: selectedSection === 'experience' }">
            <i class="fas fa-laptop-code"></i> <span>Deneyimlerim</span>
          </li>
          <li @click="selectSection('languages')" :class="{ active: selectedSection === 'languages' }">
            <i class="fas fa-microchip"></i> <span>Yeteneklerim</span>
          </li>
        </ul>
      </div>

      <div class="main-content fade-in">
        <h3 class="section-badge">{{ sectionTitle }}</h3>
        
        <div v-if="selectedSection === 'about'" class="content-card animated">
          <p class="about-text">{{ sectionContent }}</p>
        </div>
        
        <div v-if="selectedSection === 'education'" class="education-section animated">
          <div v-for="(edu, index) in educationList" :key="index" class="content-card">
            <h4>{{ edu.university }}</h4>
            <div class="timeline-meta">
              <span><i class="far fa-calendar-alt"></i> {{ edu.start }} - {{ edu.end }}</span>
            </div>
            <p class="courses"><strong>Aldığım Eğitimler:</strong> {{ edu.courses.join(', ') }}</p>
          </div>
        </div>
        
        <div v-if="selectedSection === 'experience'" class="experience-section animated">
          <div v-for="(exp, index) in experienceList" :key="index" class="content-card">
            <h4>{{ exp.company }}</h4>
            <div class="timeline-meta">
              <span class="position-badge">{{ exp.position }}</span>
              <span><i class="far fa-calendar-alt"></i> {{ exp.start }} - {{ exp.end }}</span>
            </div>
            <p class="projects">
  <strong>Projeler:</strong><br>
  <span v-for="(proj, i) in exp.projects" :key="i">
    {{ proj }}<br>
  </span>
</p>
          </div>
        </div>
        
        <div v-if="selectedSection === 'languages'" class="languages-section animated">
          <div class="content-card no-padding">
            <myLanguages />
          </div>
        </div>
      </div>
    </div>
    
    <myFooter/>
  </div>
</template>


<script>

import myFooter from '../components/Footer.vue';
import myNavbar from '../components/Navbar.vue';
import myLanguages from '../components/Languages.vue';

export default {
  name: 'mAbout',
  components: {
    myNavbar,
    myLanguages,
    myFooter,
  },
  data() {
    return {
      selectedSection: 'about',
      isSidebarVisible: false,
      isMobile: window.innerWidth <= 768,
      sections: {
        about: {
          title: 'Hakkımda',
          content: 'Ben Ali Tolga Çakir, yazılım geliştirme alanında tutkulu bir geliştiriciyim. Modern web ve mobil uygulama geliştirme üzerine geniş bir deneyime sahibim. Projelerimde kullanıcı deneyimini her zaman öncelikli hedefim olarak görüyorum.',
        },
      },
      educationList: [
        {
          university: 'Çankırı Karatekin Üniversitesi',
          start: '2021',
          end: '2025',
          courses: [ 'Web Geliştirme', 'Mobil Uygulama Geliştirme', 'Makine Öğrenmesi','Veri Tabanı Sistemleri'],
        },
      ],
     experienceList: [
  {
    company: 'Podiumon Mobil Uygulaması',
    position: 'Software Developer',
    start: '01.09.2025',
    end: 'Present',
    projects: [
      'iOS ve Android için React Native kullanarak çapraz platform mobil uygulama geliştirdim; mesajlaşma, post paylaşımı, bildirimler, ana keşfet sayfası ve çoklu dil desteği gibi tüm temel sosyal medya özelliklerini entegre ettim.',
      '.NET backend ile RESTful API entegrasyonu ve frontend-backend veri akışının sorunsuz çalışmasını sağladım.',
      'Kullanıcı dostu ve sezgisel arayüz tasarlayarak mobil deneyimi optimize ettim.',
    ],
  },
  {
    company: 'Hangi Koltuk Web Sitesi',
    position: 'Software Developer',
    start: '01.09.2025',
    end: 'Present',
    projects: [
      'React.js ve .NET backend kullanarak web platformu geliştirdim; hem admin paneli hem de kullanıcı arayüzünü tasarladım.',
    'UI/UX tasarımı ile kullanıcı deneyimini iyileştirdim.',
    'Frontend-backend veri akışını güvenli ve hızlı hâle getirdim.',
    ],
  },
  {
    company: 'Softtech',
    position: 'Software Developer Intern',
    start: '01.08.2025',
    end: '30.09.2025',
    projects: [
      '.NET ile backend uygulamaları geliştirdim, API entegrasyonları ve veritabanı işlemlerini yönettim.',
      'Katmanlı mimari ve SOLID prensiplerini uyguladım, CI/CD süreçlerine katkıda bulundum.',
      'Docker kullanarak geliştirme ve üretim ortamlarını yönettim.',
    ],
  },
  {
    company: 'Nivusoft',
    position: 'Software Support Intern',
    start: '01.07.2025',
    end: '31.08.2025',
    projects: [
      'Teknik destek sağladım, müşteri taleplerini yanıtladım, uygulama hatalarını raporladım ve yazılım/sistem sorunlarını çözdüm.',
    ],
  },
  {
    company: 'Narksoft',
    position: 'Software Developer Intern',
    start: '01.01.2024',
    end: '31.05.2024',
    projects: [
      'Vue.js framework kullanarak dinamik ve responsive web uygulamaları geliştirdim.',
    ],
  },
  {
    company: 'Farktor Yazılım',
    position: 'Software Developer Intern',
    start: '01.06.2023',
    end: '31.08.2023',
    projects: [
      'React.js kullanarak kullanıcı dostu ve ölçeklenebilir arayüzler geliştirdim.',
      'Bileşen tabanlı mimari benimsedim, state yönetimi için Redux veya Context API kullandım.',
    ],
  },
],
    };
  },
  computed: {
    sectionTitle() {
      switch (this.selectedSection) {
        case 'about':
          return this.sections.about.title;
        case 'education':
          return 'Eğitimim';
        case 'experience':
          return 'Deneyimlerim';
        default:
          return '';
      }
    },
    sectionContent() {
      return this.selectedSection === 'about' ? this.sections.about.content : '';
    },
  },
  methods: {
    selectSection(section) {
      this.selectedSection = section;
      if (this.isMobile) {
        this.isSidebarVisible = false; 
      }
    },
    toggleSidebar() {
      this.isSidebarVisible = !this.isSidebarVisible; 
    },
  },
  watch: {
    '$route'() {
      this.isMobile = window.innerWidth <= 768; 
    },
  },
};
</script>

<style scoped>
.page-wrapper {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background-color: var(--bg-primary);
}

.nav-container {
  z-index: 1001;
}

.content-container {
  display: flex;
  flex: 1;
  width: 100%;
  max-width: 1400px;
  margin: 0 auto;
  padding-top: 100px;
  position: relative;
}

.sidebar-wrapper {
  width: 280px;
  background-color: var(--bg-glass);
  backdrop-filter: blur(10px);
  padding: 40px 20px;
  flex-shrink: 0;
  border-right: var(--border-glass);
  transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  margin-right: 40px;
  border-radius: 0 var(--radius-lg) var(--radius-lg) 0;
}

.sidebar-menu {
  list-style-type: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.sidebar-menu li {
  padding: 15px 20px;
  cursor: pointer;
  display: flex;
  align-items: center;
  font-size: 1.1rem;
  color: var(--text-muted);
  border-radius: var(--radius-md);
  transition: var(--transition);
  font-weight: 500;
}

.sidebar-menu li i {
  margin-right: 15px;
  font-size: 1.2rem;
  width: 24px;
  text-align: center;
}

.sidebar-menu li:hover {
  background-color: rgba(255, 255, 255, 0.05);
  color: var(--text-main);
  transform: translateX(5px);
}

.sidebar-menu li.active {
  background: var(--accent-gradient);
  color: var(--text-main);
  font-weight: 600;
  box-shadow: var(--shadow-md);
}

.main-content {
  flex: 1;
  padding: 40px;
  max-width: 900px;
}

.section-badge {
  display: inline-block;
  padding: 8px 20px;
  background: rgba(56, 189, 248, 0.1);
  color: var(--accent-primary);
  border-radius: var(--radius-full);
  font-size: 1rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  margin-bottom: 30px;
  border: 1px solid rgba(56, 189, 248, 0.2);
}

.content-card {
  background: var(--bg-secondary);
  border: var(--border-glass);
  border-radius: var(--radius-lg);
  padding: 40px;
  margin-bottom: 25px;
  box-shadow: var(--shadow-sm);
  transition: var(--transition);
}

.content-card:hover {
  box-shadow: var(--shadow-md);
  border-color: rgba(255, 255, 255, 0.15);
}

.content-card.no-padding {
  padding: 0;
  background: transparent;
  border: none;
  box-shadow: none;
}

.about-text {
  font-size: 1.2rem;
  color: var(--text-muted);
  line-height: 1.8;
}

.content-card h4 {
  margin: 0 0 15px 0;
  font-size: 1.8rem;
  color: var(--text-main);
  font-weight: 700;
}

.timeline-meta {
  display: flex;
  align-items: center;
  gap: 15px;
  margin-bottom: 20px;
  font-size: 0.95rem;
  color: var(--text-muted);
}

.position-badge {
  background: var(--accent-gradient);
  color: var(--text-main);
  padding: 4px 12px;
  border-radius: var(--radius-full);
  font-weight: 600;
  font-size: 0.9rem;
}

.courses, .projects {
  font-size: 1.1rem;
  color: var(--text-muted);
  line-height: 1.6;
}

.courses strong, .projects strong {
  color: var(--text-main);
  margin-right: 5px;
}

.toggle-button {
  display: none;
  background: var(--accent-gradient);
  color: white;
  border: none;
  cursor: pointer;
  font-size: 20px;
  width: 45px;
  height: 45px;
  border-radius: 50%;
  box-shadow: var(--shadow-md);
}

.fade-in {
  animation: fadeIn 0.5s ease-out;
}

.animated {
  animation: slideUp 0.6s cubic-bezier(0.2, 0.8, 0.2, 1) forwards;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

@media (max-width: 900px) {
  .content-container {
    flex-direction: column;
    padding-top: 80px;
  }

  .sidebar-wrapper {
    position: fixed;
    top: 0;
    left: 0;
    width: 280px;
    height: 100vh;
    z-index: 1050;
    transform: translateX(-100%);
    box-shadow: var(--shadow-md);
    margin-right: 0;
    border-radius: 0;
  }

  .sidebar-wrapper.open {
    transform: translateX(0);
  }

  .main-content {
    padding: 20px;
    max-width: 100%;
  }

  .toggle-button {
    display: flex;
    align-items: center;
    justify-content: center;
    position: fixed;
    bottom: 30px;
    right: 30px;
    z-index: 1060;
  }
}
</style>

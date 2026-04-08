<template>
  <div class="languages">
    <h2 class="section-title">Yeteneklerim</h2>
    <div class="skills-grid">
      <div class="language-card" v-for="language in languages" :key="language.name">
        <div class="language-header">
          <span class="language-name">{{ language.name }}</span>
          <span class="language-level">{{ language.level }}/5</span>
        </div>
        <div class="progress-bar-container">
          <div class="progress-bar-fill" :style="{ width: (language.level / 5) * 100 + '%' }"></div>
        </div>
      </div>
    </div>
  </div>
</template>
  
  <script>
  export default {
    name: 'myLanguages',
    data() {
      return {
        languages: [
          { name: 'c#', level: 4 },
          { name: '.Net', level: 4 },
          { name: 'Java', level: 3 },
          { name: 'SQL', level: 4 },
          { name: 'Javascript', level: 4 }, 
          { name: 'React', level: 4 },
          { name: 'React Native', level: 4 },
          { name: 'html css', level: 4 },
        ],
      };
    },
  };
  </script>
  
  <style scoped>
.languages {
  text-align: center;
  padding: 20px 0;
}

.section-title {
  font-size: 2.2rem;
  margin-bottom: 30px;
  background: var(--accent-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: 700;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
  max-width: 1000px;
  margin: 0 auto;
}

.language-card {
  background-color: var(--bg-secondary);
  border: var(--border-glass);
  border-radius: var(--radius-lg);
  padding: 20px;
  transition: var(--transition);
  position: relative;
  overflow: hidden;
}

.language-card:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-md), var(--shadow-glow);
  border-color: rgba(56, 189, 248, 0.5);
}

.language-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 15px;
}

.language-name {
  font-size: 1.2rem;
  font-weight: 600;
  color: var(--text-main);
}

.language-level {
  font-size: 0.9rem;
  color: var(--text-muted);
  font-weight: 500;
}

.progress-bar-container {
  width: 100%;
  height: 8px;
  background-color: rgba(255, 255, 255, 0.05);
  border-radius: var(--radius-full);
  overflow: hidden;
}

.progress-bar-fill {
  height: 100%;
  background: var(--accent-gradient);
  border-radius: var(--radius-full);
  transition: width 1s cubic-bezier(0.4, 0, 0.2, 1);
}

@media (max-width: 768px) {
  .skills-grid {
    grid-template-columns: 1fr;
    padding: 0 15px;
  }
}
</style>
  
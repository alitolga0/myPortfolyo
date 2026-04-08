<template>
  <nav>
    <div class="navbar-container">
      <div class="menu-toggle" @click="toggleMenu">
        <div class="bar" :class="{ 'active': isMenuOpen }"></div>
        <div class="bar" :class="{ 'active': isMenuOpen }"></div>
        <div class="bar" :class="{ 'active': isMenuOpen }"></div>
      </div>
      <div class="logo">
        <i class="fas fa-laptop-code"></i>
      </div>
      <ul class="navbar" :class="{ 'active': isMenuOpen }">
        <li v-for="(link, index) in links" :key="index" class="nav-item">
          <router-link :to="link.path" class="nav-link" @click="closeMenu">
            {{ link.name }}
          </router-link>
        </li>
      </ul>
    </div>
    <div class="sidebar" :class="{ 'active': isMenuOpen }">
      <ul class="dropdown-menu">
        <li v-for="(link, index) in links" :key="index" class="dropdown-item">
          <router-link :to="link.path" class="nav-link" @click="closeMenu">
            {{ link.name }}
          </router-link>
        </li>
      </ul>
    </div>
  </nav>
</template>
<script>
export default {
  name: 'myNavbar',
  data() {
    return {
      links: [
        { name: 'Anasayfa', path: '/' },
        { name: 'Hakkımda', path: '/about' },
        { name: 'Hizmetler', path: '/services' },
        { name: 'İletişim', path: '/contact' },
      ],
      isMenuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
    closeMenu() {
      this.isMenuOpen = false;
    },
  },
};
</script>
<style scoped>
nav {
  background-color: var(--bg-glass);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  padding: 15px 30px;
  position: fixed; 
  top: 0; 
  left: 0; 
  right: 0; 
  z-index: 1000; 
  border-bottom: var(--border-glass);
  box-shadow: var(--shadow-sm); 
  transition: var(--transition);
}

.navbar-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}

.menu-toggle {
  display: none; 
  flex-direction: column;
  cursor: pointer;
  z-index: 1100;
}

.logo {
  color: var(--text-main);
  font-size: 28px;
  font-weight: 800;
  display: flex;
  align-items: center;
  gap: 10px;
}

.logo i {
  background: var(--accent-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.navbar {
  list-style: none;
  display: flex;
  margin: 0;
  transition: max-height 0.3s ease;
  overflow: hidden;
}

.nav-item {
  margin: 0 10px;
}

.nav-link {
  color: var(--text-muted);
  text-decoration: none;
  padding: 8px 16px;
  border-radius: var(--radius-full);
  transition: var(--transition);
  font-size: 16px;
  font-weight: 500;
}

.nav-link:hover, .nav-link.router-link-active {
  color: var(--text-main);
  background-color: rgba(255, 255, 255, 0.1);
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.1);
}

.sidebar {
  position: fixed;
  top: 0;
  right: -300px; 
  width: 300px;
  height: 100vh;
  background-color: var(--bg-secondary);
  box-shadow: -10px 0 30px rgba(0, 0, 0, 0.5); 
  transition: right 0.4s cubic-bezier(0.4, 0, 0.2, 1); 
  z-index: 1050; 
  padding-top: 80px;
}

.sidebar.active {
  right: 0; 
}

.dropdown-menu {
  list-style: none; 
  padding: 0; 
  margin: 0; 
  display: flex; 
  flex-direction: column; 
}

.dropdown-item {
  padding: 10px 20px;
}

.dropdown-item .nav-link {
  display: block;
  padding: 15px;
  border-radius: var(--radius-md);
  font-size: 18px;
}

.bar {
  width: 30px;
  height: 3px;
  background-color: var(--text-main);
  margin: 6px 0;
  border-radius: 3px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.menu-toggle .bar.active:nth-child(1) {
  transform: translateY(9px) rotate(45deg);
}

.menu-toggle .bar.active:nth-child(2) {
  opacity: 0;
}

.menu-toggle .bar.active:nth-child(3) {
  transform: translateY(-9px) rotate(-45deg);
}

@media (max-width: 768px) {
  .navbar {
    display: none; 
  }
  .menu-toggle {
    display: flex; 
  }
}
</style>

<template>
  <div id="app">
    
    <router-view></router-view>
  </div>
</template>

<script>


export default {
  name: 'App',
  components: {
    
  }
};
</script>

<style>
:root {
  --bg-primary: #0f172a;       /* Deep slate for premium look */
  --bg-secondary: #1e293b;
  --bg-glass: rgba(30, 41, 59, 0.7);
  
  --text-main: #f8fafc;
  --text-muted: #94a3b8;
  
  --accent-primary: #38bdf8;   /* Vibrant blue */
  --accent-secondary: #818cf8; /* Soft indigo */
  --accent-gradient: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
  
  --shadow-sm: 0 4px 6px -1px rgba(0, 0, 0, 0.3);
  --shadow-md: 0 10px 15px -3px rgba(0, 0, 0, 0.4);
  --shadow-glow: 0 0 20px rgba(56, 189, 248, 0.3);
  
  --border-glass: 1px solid rgba(255, 255, 255, 0.1);
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-full: 9999px;
  
  --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Outfit', sans-serif;
  background-color: var(--bg-primary);
  color: var(--text-main);
  line-height: 1.6;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

a {
  text-decoration: none;
  color: inherit;
  transition: var(--transition);
}

button {
  font-family: inherit;
}
</style>

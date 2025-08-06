<template>
  <div>
    <Navbar @navigate="setCurrentComponent" />
  </div>
  <header :class="backgroundClass">
    <component :is="currentComponent" />
  </header>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Program from './components/Program.vue'
import Information from './components/Info.vue'
import Home from './components/Home.vue'
import About from './components/About.vue'

export default {
  components: {
    Navbar,
    Program,
    Information,
    Home,
    About
  },
  data() {
    return {
      currentComponent: 'Home'
    }
  },
  computed: {
    backgroundClass() {
      switch (this.currentComponent) {
        case 'Program':
          return 'bg-program'
        case 'Home':
          return 'bg-about'
        case 'Information':
          return 'bg-info'
        case 'About':
          return 'bg-about'
        default:
          return 'bg-about'
      }
    }
  },

  methods: {
    setCurrentComponent(name) {
      this.currentComponent = name
    }
  }
}
</script>

<style>
.bg-program {
  height: 185vh;
  background: url(src/assets/background4.png);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}

.bg-about {
  height: 100vh;
  background: url(src/assets/background.png);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}

.bg-info {
  height: 130vh;
  background: url(src/assets/background.png);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}

/* Tablets (max-width: 1024px) */
@media (max-width: 800px) {
  header {
    height: 150vh;
    background-position: -400px;
  }
}


/* Small phones (max-width: 480px) */
@media (max-width: 400px) {
  header {
    height: 170vh;
    background-position: -400px;
  }
}
</style>

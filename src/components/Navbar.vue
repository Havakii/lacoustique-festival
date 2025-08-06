<template>
  <div class="app">
    <div class="bg-transparent lg:bg-transparent fixed w-full z-50 navbar">
      <div class="flex items-center justify-between py-4 z-50">
        <div v-if="!darkMode">
          <h3 class="hidden sm:block text-2xl font-semibold ml-10 text-black title-logo">
            Lacoustique
          </h3>
        </div>
        <div v-else>
          <h3 class="hidden sm:block text-2xl font-semibold ml-10 text-white title-logo">
            Lacoustique
          </h3>

        </div>

        <div class="hidden sm:flex sm:items-center">
          <ul class="flex space-x-4 mr-8">
            <li v-for="(link, index) in navigationLinks" :key="index">
              <button @click="handleNavClick(link.path)" :class="[
                'px-2 uppercase font-semibold',
                darkMode ? 'text-white' : 'text-black'
              ]">
                {{ link.label }}
              </button>
            </li>
          </ul>
        </div>

        <h3
          class="sm:hidden md:hidden lg:hidden font-semibold pl-10 text-start text-2xl drop-shadow-md text-white title-logo">
          Lacoustique
        </h3>

        <button class="sm:hidden cursor-pointer" @click="toggleNav">
          <svg v-if="showNav" xmlns="http://www.w3.org/2000/svg" class="h-7 w-7 mr-3 text-white" fill="none"
            viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
          </svg>
          <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-7 w-7 mr-3 text-white" fill="none" viewBox="0 0 24 24"
            stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h8m-8 6h16" />
          </svg>
        </button>
      </div>

      <div class="bg-primary z-5 w-screen" :class="{ hidden: !showNav, absolute: showNav }">
        <div class="flex flex-col sm:hidden">
          <ul class="p-3 text-center text-md bg-transparent">
            <li v-for="(link, index) in navigationLinks" :key="index" class="py-3 mx-4">
              <button @click="handleNavClick(link.path)" :class="[
                'px-2 uppercase font-semibold',
                darkMode ? 'text-white' : 'text-black'
              ]">
                {{ link.label }}
              </button>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showNav: false,
      darkMode: false, 
      navigationLinks: [
        { label: 'Accueil', path: 'Home' },
        { label: 'Programme', path: 'Program' },
        { label: 'A propos', path: 'About' },
        { label: 'Infos pratiques', path: 'Information' }
      ]
    }
  },
  methods: {
    toggleNav() {
      this.showNav = !this.showNav
    },
    handleNavClick(path) {
      this.darkMode = (path === 'Program') // Activate dark mode only on Program page
      this.$emit('navigate', path)
      this.showNav = false
    }
  }
}
</script>

<style>
@font-face {
  font-family: hamurz;
  src: url('@/assets/hamurz.ttf');
}

.title-logo {
  font-family: hamurz;
}

.navbar {
  background-color: #244673;
}
</style>

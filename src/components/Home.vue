<template>
  <div class="flex justify-center pt-16 ">
    <div class="text-center pt-10">
      <div v-for="(item, index) in about" :key="index" class="festival-title">
        <h2 class="text-3xl font-bold mb-2 custom-font pt-12">{{ item.title }}</h2>
        <p class="text-2xl font-semibold">{{ item.date }}</p>
        <p class="text-2xl font-semibold">{{ item.place }}</p>
      </div>
    </div>
  </div>
  <div class="flex justify-center">
    <div class="font-festival text-center max-w-xl ">
      <span class="festival-artists font-semibold" v-for="(artist, index) in artists" :key="index">
        {{ artist }}<span v-if="index < artists.length - 1"> / </span>
      </span>
    </div>
  </div>
</template>



<script>

export default {
  data() {
    return {
      about: [{
        title: 'Lac\'oustique festival',
        date: '29 - 30 août 2025',
        place: 'Lac de Marcenac'
      }],
      artists: [
        'Myasara',
        'Do Not Do',
        'Tiwiza',
        'Djset avec Sara & Europe',
        'LA GRANJA',
        'DUO ARAËLLES'
      ]
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@400;600;800&display=swap');

.custom-font {
  font-family: 'hamurz', sans-serif;
  font-size: 60px;
}
.font-festival {
  padding-top: 130px;
  font-family: 'Oswald';
  letter-spacing: 1px;
  font-size: 24px;
  color: white;
  font-weight: bold;
}


/* Tablets (max-width: 1024px) */


@media (max-width: 1200px) {
  .festival-title {
    padding-top: 100px;
  }

  .font-festival {
      padding-top: 300px;
  }

  .festival-artists {
    padding-top: 1000px;
  }
}


/* Small phones (max-width: 480px) */
@media (max-width: 400px) {
.festival-title {
    padding-top: 100px;
  }

  .festival-artists {
    padding-top: 100px;
  }
}
</style>

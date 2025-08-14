<template>
  <div class="flex justify-center pt-16 ">
    <div class="text-center">
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

.festival-title {
  padding-top: 50px;
}
.font-festival {
  padding-top: 150px;
  font-family: 'Oswald';
  letter-spacing: 1px;
  font-size: 24px;
  color: white;
  font-weight: bold;
}


/* Tablets (max-width: 1024px) */


@media (max-width: 1000px) {
  .festival-title {
    padding-top: 120px;
  }

  .font-festival{
      padding: 20px;
      padding-top: 250px;
  }

}

@media (max-width: 600px) {
  .custom-font {
      line-height: 1;
  }
  .festival-title {
    padding-top: 50px;
  }
}


/* Small phones (max-width: 480px) */
@media (max-width: 400px) {
  .festival-title {
      padding-top: 20px;
    }
.font-festival {
    padding-top: 140px;
  }


}
</style>

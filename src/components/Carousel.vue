<template>
    <v-carousel cycle hide-delimiter-background :show-arrows="false">
        <v-carousel-item v-for="(image, i) in slides" :key="i">
            <v-img :src="image" height="carouselSize"></v-img>
        </v-carousel-item>
    </v-carousel>
</template>

<script>
import image1 from '@/assets/1.png'
import image3 from '@/assets/3.png'
import image4 from '@/assets/4.png'
import image5 from '@/assets/5.png'
import image6 from '@/assets/6.png'
import image7 from '@/assets/7.png'

export default {
    data() {
        return {
            carouselSize: 80,
            slides: [
                image1,
                image3,
                image4,
                image5,
                image6,
                image7
            ]
        }
    }
}
</script>

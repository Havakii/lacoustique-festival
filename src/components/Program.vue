<template>
    <div class="p-6 pt-12">
        <v-row class="mb-12 pt-8" align="center">
            <!-- Left empty spacer -->
            <v-col cols="2"></v-col>

            <!-- Centered day buttons container -->
            <v-col cols="8">
                <v-row justify="center" no-gutters>
                    <v-col v-for="(day, index) in days" :key="index" cols="auto" class="px-2">
                        <v-btn rounded="xl" size="large" :color="selectedDay === day.date ? '#D29DCC' : 'transparent'"
                            :class="{
                                'text-white': true,
                                'border': true,
                                'hover:bg-[#D29DCC]': selectedDay !== day.date,
                            }" style="border-width: 1px; border-color: white;" @click="selectedDay = day.date">
                            {{ day.label }}
                        </v-btn>
                    </v-col>
                </v-row>
            </v-col>

            <!-- Right aligned download button -->
            <v-col cols="2" class="d-flex justify-end">
                <v-btn class="ma-1" color="indigo-lighten-2" href="/programme.pdf" download target="_blank"
                    icon="mdi-download">
                </v-btn>

            </v-col>
        </v-row>




        <!-- Vuetify Timeline -->
        <v-timeline align="center" line-color="grey-lighten-3" line-thickness="1" truncate-line="both">
            <v-timeline-item v-for="(event, i) in program[selectedDay]" :key="i" :dot-color="dotColor" size="xsmall"
                max-width="400px">
                <div>
                    <h2 class="mt-n1 headline font-weight-bold mb-4 text-cyan-accent-3">
                        {{ event.time }}
                    </h2>
                    <div class="custom-font-program text-white">
                        {{ event.title }}
                    </div>
                </div>
            </v-timeline-item>
        </v-timeline>
    </div>
    <div v-if="selectedDay === '2025-08-29'" class="pt-12">
        <Carousel />
    </div>
</template>

<script>
import Carousel from './Carousel.vue';
export default {
    components: {
        Carousel
    },
    data() {
        return {
            dotColor: '#D29DCC',
            selectedDay: '2025-08-29',
            days: [
                { date: '2025-08-29', label: 'Vendredi 29 août' },
                { date: '2025-08-30', label: 'Samedi 30 août' }
            ],
            program: {
                '2025-08-29': [
                    { time: '17h30', title: 'Contes franco-occitans (dès 3 ans) – Justin Thérondel' },
                    { time: '19h00', title: 'Restauration – Saveurs du Monde Lalbenque' },
                    { time: '20h00', title: 'Concert celtique – Reprises de musiques de films avec DUO ARAËLLES' },
                    { time: '21h00', title: 'Cinélot sous les étoiles : “L\'envolée sauvage” (1h50) + court “Mamie, le soleil et la pluie”' }
                ],
                '2025-08-30': [
                    { time: '08h00-17h00', title: 'Vide-greniers & vide-dressing en fanfare – LA GRANJA' },
                    { time: '11h00', title: 'Balade cueillette de plantes sauvages (1h / 3,5km) – Claire Mauquié' },
                    { time: '12h00', title: 'Grand buffet anti-gaspi avec les chef.fes de l’asso' },
                    { time: '14h00', title: 'Atelier linogravure – Matière Grasse & La Tresse' },
                    { time: '15h00', title: 'Balade cueillette (2e session) / Concours de troc (dès 6 ans)' },
                    { time: '17h30', title: 'Table ronde “L’écologie, un truc de citadins ?” – Fanny Hugues, sociologue' },
                    { time: 'Toute la journée', title: 'Expo photo – Rétrospective du Lacoustique par Caroline Peyronel' },
                    { time: '19h00', title: 'Restauration sur place – Snack local et gourmand avec les chef.fes' },
                    { time: '20h30', title: 'Soirée concerts (participation libre) : Myasara (Soul), Do Not Do (Pop rock), Tiwiza (Rock amazighes), DJ set Sara & Europe' }
                ]
            }
        }
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200..700&display=swap');

.custom-font-program {
    font-family: 'Oswald', sans-serif;
    font-size: 20px;
}
</style>

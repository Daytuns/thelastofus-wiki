<template>
  <section class="card-collection-block h-screen flex items-center justify-center p-10 flex-col text-white">
    <img
        src="../assets/GamesBG.png"
        alt="Games Background"
        class="absolute w-full h-full object-cover z-0"
    />
    <h2 class="oswald text-4xl mb-4 font-bold z-1">DISCOVER THE LAST OF US</h2>

    <div class=" mx-auto max-w-screen-xl px-4 py-10 z-1">
        <div class="simple-carousel simple-carousel--same-height">
        <div class="simple-carousel-content overflow-x-auto">
            <div class="flex gap-6 snap-x snap-mandatory scroll-smooth pb-4">
            <GameCard
                v-for="(game, index) in games"
                :key="index"
                :game="game"
            />
            </div>
        </div>
        </div>
    </div>
    </section>

</template>

<script setup>
import GameCard from './GameCard.vue'


const games = [
  {
    title: 'The Last of Us Complete',
    image: new URL('../assets/games/complete.webp', import.meta.url).href,
    description: 'Go back to the beginning and experience the award-winning games in one complete collection.',
    date: '10/04/2025'
  },
  {
    title: 'The Last of Us Part II Remastered',
    image: new URL('../assets/games/TwoRemastered.webp', import.meta.url).href,
    description: 'Experience Ellie and Abby’s story with new visuals and features. Now on PS5 and PC.',
    date: '19/01/2024'
  },
  {
    title: 'Part II: No Return',
    image: new URL('../assets/games/PartTwoRemastered.webp', import.meta.url).href,
    description: 'Survive roguelike encounters in the new No Return mode with random challenges.',
    date: '19/01/2024'
  },
  {
    title: 'The Last of Us Part I',
    image: new URL('../assets/games/Part1.webp', import.meta.url).href,
    description: 'Relive the game that started it all. Rebuilt for PS5 and PC.',
    date: '02/09/2022'
  },
  {
    title: 'The Last of Us Part II',
    image: new URL('../assets/games/Part2.webp', import.meta.url).href,
    description: 'Face the devastating physical and emotional repercussions of Ellie’s actions.',
    date: '06/19/2020'
  },
  {
    title: 'The Last of Us Remastered',
    image: new URL('../assets/games/Remastered.webp', import.meta.url).href,
    description: 'The Last of Us™, winner of over 200 Game of the Year awards, has been rebuilt for the PlayStation®4 console. It now features high-resolution, full 1080p character models, improved shadows and lighting, and several other gameplay enhancements.',
    date: '07/22/2024'
  },
  {
    title: 'The Last of Us: Left Behind',
    image: new URL('../assets/games/LeftBehind.webp', import.meta.url).href,
    description: 'The Last of Us: Left Behind combines themes of survival, loyalty, and love with tense action-survival gameplay in this critically acclaimed chapter.',
    date: '07/22/2024'
  },
]
</script>

<style scoped>

</style>

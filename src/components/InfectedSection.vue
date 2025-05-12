<script setup>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { ref, nextTick, onMounted } from "vue";

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  gsap.to("#right-bg", {
    scrollTrigger: {
      trigger: "#left-image",
      start: "60% bottom",
      end: "center center",
      scrub: 1,
    },
    opacity: 1,
  });

  gsap.to(".left p", {
    scrollTrigger: {
      trigger: "#left-image",
      start: "60% bottom",
      end: "center center",
      scrub: 1,
    },
    opacity: 1,
  });

  gsap.to(".infected-wrapper", {
    scrollTrigger: {
      trigger: "#left-image",
      start: "60% bottom",
      end: "center center",
      scrub: 1,
    },
    opacity: 1,
    color: "#7F7E7E",
  });

  gsap.to(".infected-description", {
    scrollTrigger: {
      trigger: "#left-image",
      start: "100% bottom",
      end: "center center",
      scrub: true,
    },
    opacity: 1,
  });
});

const infected = [
  {
    name: 'RUNNER',
    picture: new URL('../assets/infected/Runner.webp', import.meta.url).href,
    description: `Runners are the first stage of the infected, transformed shortly after exposure. They're aggressive and fast but retain some human characteristics.`
  },
  {
    name: 'STALKER',
    picture: new URL('../assets/infected/Stalker.webp', import.meta.url).href,
    description: `Stalkers are stealthy infected that use cover and ambush tactics. They're a midpoint between Runners and Clickers.`
  },
  {
    name: 'CLICKER',
    picture: new URL('../assets/infected/Clicker.webp', import.meta.url).href,
    description: `Clickers are blind infected that use echolocation to navigate. Their heads are fully consumed by fungal growth and they’re highly dangerous.`
  },
  {
    name: 'BLOATER',
    picture: new URL('../assets/infected/Bloater.webp', import.meta.url).href,
    description: `Bloaters are heavily armored infected with decades of fungal growth. They throw spore bombs and can absorb massive damage.`
  },
  {
    name: 'SHAMBLER',
    picture: new URL('../assets/infected/Shambler.webp', import.meta.url).href,
    description: `Shamblers are similar to Bloaters but burst with acid clouds, burning anyone nearby.`
  },
  {
    name: 'RAT KING',
    picture: new URL('../assets/infected/RatKing.webp', import.meta.url).href,
    description: `The Rat King is a massive, horrifying fusion of multiple infected, acting as a terrifying boss in The Last of Us Part II.`
  }
];

const selectedInfected = ref(null);
const infectedBG = new URL('../assets/infected/infectedbg1.png', import.meta.url).href;
const infectedOverlayBG = new URL('../assets/charactersBG1.webp', import.meta.url).href;

let infectedPicTween;

function selectInfected(unit) {
  selectedInfected.value = unit;

  nextTick(() => {
    if (infectedPicTween) {
      infectedPicTween.scrollTrigger.refresh();
    } else {
      infectedPicTween = gsap.to("#infectedPic", {
        scrollTrigger: {
          trigger: "#left-image",
          start: "60% bottom",
          end: "center center",
          scrub: 1
        },
        opacity: 1
      });
    }
  });
}
</script>

<template>
  <div class="main-container bg-black flex h-screen z-11">
     <!-- Left Panel -->
    <div class="left h-screen w-1/2 flex justify-center items-center bg-black flex-col z-11">
      <!-- Title -->
      <div class="font-light mr-57 p-2.5 text-white roboto z-12">
        <p class="opacity-0">INFECTED</p>
      </div>

      <!-- Infected Grid -->
      <div class="grid grid-cols-2 w-1/2 gap-5 mt-10 ml-40 opacity-0 relative infected-wrapper">
        <div class="text-[#7F7E7E] text-sm hover:text-red-400 cursor-pointer"
          v-for="unit in infected"
          :key="unit.name"
          @click="selectInfected(unit)">
          {{ unit.name }}
        </div>
      </div>
    </div>

    <!-- Right Panel -->
    <div class="right flex align-center w-1/2 relative h-full">
      <!-- Exit Button -->
      <div class="p-15 right-0 h-5 w-5 absolute z-50 opacity-0 infected-description">
        <svg class="cursor-pointer" v-if="selectedInfected" @click="selectedInfected = null" fill="#7F7E7E" height="20px" width="20px" viewBox="0 0 460.775 460.775">
          <path d="M285.08,230.397L456.218,59.27c6.076-6.077,6.076-15.911,0-21.986L423.511,4.565c-2.913-2.911-6.866-4.55-10.992-4.55 c-4.127,0-8.08,1.639-10.993,4.55l-171.138,171.14L59.25,4.565c-2.913-2.911-6.866-4.55-10.993-4.55 c-4.126,0-8.08,1.639-10.992,4.55L4.558,37.284c-6.077,6.075-6.077,15.909,0,21.986l171.138,171.128L4.575,401.505 c-6.074,6.077-6.074,15.911,0,21.986l32.709,32.719c2.911,2.911,6.865,4.55,10.992,4.55c4.127,0,8.08-1.639,10.994-4.55 l171.117-171.12l171.118,171.12c2.913,2.911,6.866,4.55,10.993,4.55c4.128,0,8.081-1.639,10.992-4.55l32.709-32.719 c6.074-6.075,6.074-15.909,0-21.986L285.08,230.397z"/>
        </svg>
      </div>

      <!-- Background -->
      <img
        :src="selectedInfected ? infectedOverlayBG : infectedBG"
        alt="background"
        class="object-cover max-h-full opacity-0"
        id="right-bg"
      />

      <!-- Infected Image -->
      <img
        :src="selectedInfected ? selectedInfected.picture : ''"
        :alt="selectedInfected ? selectedInfected.name : ''"
        class="object-contain max-h-3/4 absolute right-0 bottom-0 opacity-0 z-12"
        id="infectedPic"
        loading="lazy"
      >

      <!-- Infected Description -->
      <div class="opacity-0 infected-description">
        <h1 v-if="selectedInfected" class="text-white w-1/2 h-1/2 roboto absolute top-20 left-0 ml-10 z-12" v-html="selectedInfected.name"></h1>
        <p v-if="selectedInfected" class="text-[#7F7E7E] w-1/2 h-1/2 text-base roboto absolute top-30 left-0 ml-10 z-12" v-html="selectedInfected.description"></p>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>

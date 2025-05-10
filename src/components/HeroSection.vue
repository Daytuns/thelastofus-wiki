<script setup>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { onMounted } from "vue";

gsap.registerPlugin(ScrollTrigger);
    
onMounted(() => {

  gsap.to("#JoelHero", {
    scrollTrigger: {
      trigger: "#JoelHero",
      start: "85% center",
      endTrigger: "world",
      end: "bottom 0%",
      scrub: 1,
      pin: ".background-container",
    },
    scale: 5,
    y: 220,
    opacity: 0,
    duration: 3,
  });

  gsap.to("#blackOverlay", {
  scrollTrigger: {
    trigger: "#JoelHero",
    start: "85% center",
    endTrigger: "world",
    end: "center 0%",
    scrub: 1,
  },
  opacity: 1, 
});

gsap.to("#enter", {
    scrollTrigger: {
      trigger: "#JoelHero",
      start: "85% center",
      endTrigger: "world",
      end: "center 0%",
      scrub: true,
    },
    opacity: 0,
  });


});
</script>

<template>
  <section class="relative w-full overflow-hidden bg-black world">
    <div class="relative mx-auto background-container" style="aspect-ratio: 16 / 9; width: 100%; max-width: 1920px;">
        <img
        src="../assets/HeroBG-green6.webp"
        alt="Hero Background"
        class="absolute inset-0 w-full h-full object-cover"
        />
        <div id="blackOverlay" class="absolute inset-0 bg-black opacity-0 z-30"></div>
        <img
        id="JoelHero"
        src="../assets/Joelhero.png"
        alt="Joel Hero"
        class="absolute z-20"
        style="
            left: 43.9%;
            top: 11.6%;
            width: 12.2%;
        "
        />
        <div class="opacity-75 absolute bottom-4/9 left-1/2 transform -translate-x-1/2 translate-y-1/2 text-3xl font-bold oswald text-white z-10" id="enter">
            <p>ENTER THE WORLD</p>
        </div>
        <svg
          viewBox="0 0 1024 1024"
          class="absolute bottom-2/5 left-1/2 transform -translate-x-1/2 w-5 h-5 animate-bounce"
          xmlns="http://www.w3.org/2000/svg"
          fill="#1D2A21"
        >
          <path
            d="M903.232 256l56.768 50.432L512 768 64 306.432 120.768 256 512 659.072z"
            fill="#ffffff"
          />
        </svg>
    </div>
  </section>
</template>

<style scoped>
</style>

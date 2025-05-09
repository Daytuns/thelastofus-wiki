<script setup>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { onMounted } from "vue";

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  gsap.to("#left-image", {
    scrollTrigger: {
      trigger: "#left-image",
      start: "100% bottom",
      end: "center center",
      scrub: 1,
    },
    opacity: 1,
  });

  gsap.to(".right p", {
    scrollTrigger: {
      trigger: "#left-image",
      start: "100% bottom",
      end: "center center",
      scrub: 1,
    },
    opacity: 1,
    color: "#ffffff",
  });

  gsap.to(".characters", {
    scrollTrigger: {
      trigger: "#left-image",
      start: "100% bottom",
      end: "center center",
      scrub: 1,
    },
    opacity: 1,
    color: "#7F7E7E",
  });

});

const names = [
  'JOEL MILLER', 'DINA',
  'ELLIE WILLIAMS', 'ABBY ANDERSON',
  'TOMMY MILLER', 'ISAAC DIXON',
  'SARAH MILLER', 'JESSE',
  'TESS SERVOPOULOS', 'LEV',
  'BILL', 'YARA',
  'HENRY AND SAM', 'MANNY',
  'RILEY ABEL', 'OWEN MOORE',
  'MARLENE', 'JERRY ANDERSON'
]

</script>

<template>
  <div class="main-container bg-black flex h-screen">
    <div class="left flex align-center w-1/2">
      <img src="../assets/charactersBG.png"
      class="object-cover max-h-full opacity-0" id="left-image">
    </div>
    <div class="right h-screen w-1/2 flex justify-center items-center flex-col">
      <div class="font-light mr-50 p-2.5 text-white roboto">
        <p class="opacity-0">CHARACTERS</p>
      </div>
      <div class="grid grid-cols-2 w-1/2 gap-5 mt-10 ml-40">
        <div class="characters opacity-0 text-sm" v-for="name in names" :key="name">
          {{ name }}
        </div>
      </div> 
    </div>
  </div>
</template>

<style>
</style>

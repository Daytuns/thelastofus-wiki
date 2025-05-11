<script setup>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { onMounted } from "vue";
import { ref, nextTick } from 'vue';

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  gsap.to("#left-image", {
    scrollTrigger: {
      trigger: "#left-image",
      start: "80% bottom",
      end: "center center",
      scrub: 1,
    },
    opacity: 1,
  });

  gsap.to(".right p", {
    scrollTrigger: {
      trigger: "#left-image",
      start: "80% bottom",
      end: "center center",
      scrub: 1,
    },
    opacity: 1,
  });

  gsap.to(".characters-wrapper", {
    scrollTrigger: {
      trigger: "#left-image",
      start: "80% bottom",
      end: "center center",
      scrub: 1,
    },
    opacity: 1,
    color: "#7F7E7E",
  });

  gsap.to(".character-description", {
    scrollTrigger: {
      trigger: "#left-image",
      start: "80% bottom",
      end: "center center",
      scrub: true,
    },
    opacity: 1,
  });

});

const characters = [
  {
    name: 'JOEL MILLER',
    picture: new URL('../assets/JoelMiller.webp', import.meta.url).href,
    description: `Joel Miller is the playable protagonist of The Last of Us Part I, a supporting character in The Last of Us: Left Behind and The Last of Us Part II, the latter of which he is briefly playable in, and a playable character in the No Return mode. <br><br>
    Joel was a survivor in post-apocalyptic America that had been ravaged by the Cordyceps brain infection. After losing his only daughter Sarah in the early stages of the outbreak, Joel became a ruthless and cynical smuggler eventually tasked with smuggling and protecting Ellie Williams, a young girl who was the key to mankind's survival. Joel eventually formed a strong bond with her.`
  },
  {
    name: 'DYNE',
    picture: new URL('../assets/Dina1.webp', import.meta.url).href,
    description: `Dina is a prominent character in The Last of Us Part II. She is Ellie’s close friend and romantic partner. Dina accompanies Ellie on her journey for revenge and provides emotional support throughout their time in Seattle. <br><br>Like Ellie, she was orphaned at a young age and forced to survive on her own and be self-sufficient. Her strong moral compass and honest nature bring out the best in Ellie.`
  },
  {
    name: 'ELLIE WILLIAMS',
    picture: new URL('../assets/EllieWilliams.webp', import.meta.url).href,
    description: `When we first meet Ellie, she's a 14-year-old girl who hasn't known the "normal" world before 2013. Therefore, Joel becomes not just her transport… but also a guide to the world. She's precocious, witty, and capable. Whether it's with her wordplay or overcoming crises, her cunning and resourcefulness prove invaluable. <br><br>
    Five years later, we reunite with Ellie in The Last of Us Part II. She's more confident, honest, and stronger. When a traumatic event rocks her and her community, she embarks on a journey of revenge. Though she's matured, she must grapple not only with her adversaries, both human and infected, but also with the emotional burden of her actions.`
  },
  {
    name: 'ABBY ANDERSON',
    picture: new URL('../assets/AbbyAndrson1.webp', import.meta.url).href,
    description: `When we first meet Abby in The Last of Us Part II, she's a key member of the WLF. Despite her reputation as a formidable fighter, she masks her vulnerability beneath a stoic and commanding presence. She and her father were once members of the Fireflies until, following a tragic accident, Abby was left alone. Now she must find her identity, meaning, and purpose beyond her need for justice.`
  },
  {
    name: 'TOMMY MILLER',
    picture: new URL('../assets/Tommy.webp', import.meta.url).href,
    description: `Though he shares his brother Joel's ruggedness and determination, Tommy is distinguished by his impulsive, compassionate, and optimistic personality. After a time fighting alongside the Fireflies, he meets his future wife, Maria, and her community in Jackson, Wyoming. With this newfound sense of values, he seeks to create a rich and meaningful life despite daunting circumstances. <br><br>
    In The Last of Us Part II, Elli and Joel join Maria and Tommy's community. Tommy continues his personal mission, patrolling and leading the community alongside Maria, and also welcomes Ellie into his family.`
  },
  {
    name: 'ISAAC DIXON',
    picture: new URL('../assets/IsaacDixon.webp', import.meta.url).href,
    description: `Isaac is the authoritarian leader of the Washington Liberation Front (WLF). He commands Abby and her group and is focused on winning the war against the Seraphites.`
  },
  // {
  //    name: 'SARAH MILLER',
  //    picture: new URL('../assets/SarahMiller.webp', import.meta.url).href,
  //    description: `Sarah is Joel’s teenage daughter. Her tragic death during the initial Cordyceps outbreak profoundly affects Joel and sets the tone for the rest of the series.`
  // },
  {
    name: 'JESSE',
    picture: new URL('../assets/Jesse1.webp', import.meta.url).href,
    description: `Jesse is a resident of Jackson and Dina’s ex-boyfriend. He is a loyal friend to Ellie and supports her during her mission in Seattle. <br><br>
    Jesse is a natural leader in the community with a strong moral compass. He's driven by his desire to protect those in his life. His combat experience and commanding nature make him an elite patrolman.`
  },
  {
    name: 'TESS SERVOPOULOS',
    picture: new URL('../assets/Tess.webp', import.meta.url).href,
    description: `Strong, capable, and arguably more ruthless than her smuggling partner, Joel, Tess overcame the hardships of the brutal world around her to become a skilled strategist and negotiator. Her leadership and physical prowess made her a respected figure in the Boston quarantine zone. Despite adapting to the "kill or be killed" mentality of a hardened survivor, she remains loyal and courageous, ultimately proving her selflessness by aiding Joel and Ellie's journey.`
  },
  {
    name: 'LEV',
    picture: new URL('../assets/Lev.webp', import.meta.url).href,
    description: `Lev is a young Seraphite who flees his cult with his sister Yara. <br><br>Despite the dangers of expressing his identity within his fundamentalist Seraphite community, Lev forges his own path forward, training to become a skilled warrior. He is loyal, austere, and true to his values. Previously shielded from the outside world, his worldview broadens significantly when he meets Abby.`
  },
  {
    name: 'BILL',
    picture: new URL('../assets/Bill.webp', import.meta.url).href,
    description: `Bill is the last survivor of his town, where he stayed while the other residents evacuated or succumbed to the infection. His pragmatism gave him the necessary powers to fortify his place against external threats, both human and infected. His isolation resulted in loneliness and paranoia… though he'd be the last person to admit it.`
  },
  {
    name: 'YARA',
    picture: new URL('../assets/Yara.webp', import.meta.url).href,
    description: `The eldest daughter of a fundamentalist Seraphite mother, Yara is seemingly staunchly devoted to her faith. When she meets Abby, she finds the strength to stand up for her own beliefs… and take on the role of protector of her younger brother, Lev.`
  },
  // {
  //   name: 'HENRY AND SAM',
  //   picture: new URL('../assets/HenryAndSam.webp', import.meta.url).href,
  //   description: `Henry and Sam are brothers who briefly accompany Joel and Ellie. Their tragic story highlights the harshness of the infected world.`
  // },
  // {
  //   name: 'MANNY ALVAREZ',
  //   picture: new URL('../assets/MannyAlvarez.webp', import.meta.url).href,
  //   description: `Manny is Abby’s close friend and a member of the WLF. He is known for his humor and loyalty, helping Abby throughout her journey.`
  // },
  // {
  //   name: 'RILEY ABEL',
  //   picture: new URL('../assets/RileyAbel.webp', import.meta.url).href,
  //   description: `Riley is Ellie’s best friend and first love. She appears in the Left Behind DLC, where the two share a joyful but ultimately tragic moment in an abandoned mall.`
  // },
  {
    name: 'OWEN MOORE',
    picture: new URL('../assets/OwenMoore.webp', import.meta.url).href,
    description: `Owen is a former Firefly and Abby’s ex-boyfriend. Disillusioned with violence, he dreams of a peaceful life away from the WLF.`
  },
  {
    name: 'MARLENE',
    picture: new URL('../assets/Marlene.webp', import.meta.url).href,
    description: ` Marlene has been at the forefront of the fight to overthrow the military's oppressive control of the quarantine zones. Despite her experience supporting the rebellion, she remains a gentle and compassionate person. Her background in medicine fueled her desire to save humanity—something she will pursue at any cost. <br><br>Marlene is the leader of the Fireflies and Ellie’s guardian. She tasks Joel with smuggling Ellie and ultimately faces a moral dilemma over Ellie’s fate.`
  },
  {
    name: 'JERRY ANDERSON',
    picture: new URL('../assets/JerryAnderson.webp', import.meta.url).href,
    description: `Jerry is Abby’s father and the Firefly surgeon who was set to operate on Ellie to develop a cure. His death at Joel’s hands sets the events of Part II in motion.`
  }
];



const selectedCharacter = ref(null);
const charactersBG = new URL('../assets/charactersBG.png', import.meta.url).href;
const bgChar = new URL('../assets/charactersBG1.webp', import.meta.url).href;

let characterPicTween;

function selectCharacter(character) {
  selectedCharacter.value = character;

  nextTick(() => {
    if (characterPicTween) {
      // Reset the tween instead of creating a new one
      characterPicTween.scrollTrigger.refresh();
    } else {
      // Create it once
      characterPicTween = gsap.to("#characterPic", {
        scrollTrigger: {
          trigger: "#left-image",
          start: "80% bottom",
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
  <div class="main-container bg-black flex h-screen">
    <!-- Left -->
    <div class="left flex align-center w-1/2 relative h-full">
      <!-- Exit SVG -->
      <div class="p-15 h-5 w-5 absolute z-50 opacity-0 character-description">
        <svg class="cursor-pointer" v-if="selectedCharacter" v-on:click="selectedCharacter = null" fill="#7F7E7E" height="20px" width="20px" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 460.775 460.775" xml:space="preserve"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="exit-character" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <path d="M285.08,230.397L456.218,59.27c6.076-6.077,6.076-15.911,0-21.986L423.511,4.565c-2.913-2.911-6.866-4.55-10.992-4.55 c-4.127,0-8.08,1.639-10.993,4.55l-171.138,171.14L59.25,4.565c-2.913-2.911-6.866-4.55-10.993-4.55 c-4.126,0-8.08,1.639-10.992,4.55L4.558,37.284c-6.077,6.075-6.077,15.909,0,21.986l171.138,171.128L4.575,401.505 c-6.074,6.077-6.074,15.911,0,21.986l32.709,32.719c2.911,2.911,6.865,4.55,10.992,4.55c4.127,0,8.08-1.639,10.994-4.55 l171.117-171.12l171.118,171.12c2.913,2.911,6.866,4.55,10.993,4.55c4.128,0,8.081-1.639,10.992-4.55l32.709-32.719 c6.074-6.075,6.074-15.909,0-21.986L285.08,230.397z"></path> </g></svg>
      </div>
      <!-- BG -->
      <img
        :src="selectedCharacter ? bgChar : charactersBG"
        alt="background"
        class="object-cover max-h-full opacity-0"
        id="left-image"
      />
      <!-- Character Display -->
      <img
        :src="selectedCharacter ? selectedCharacter.picture : ''"
        :alt="selectedCharacter ? selectedCharacter.name : ''"
        class="object-contain max-h-3/4 fixed left-0 bottom-0 opacity-0 z-10"
        id="characterPic"
        loading="lazy"
      >
      <div class="opacity-0 character-description">
        <h1 v-if="selectedCharacter" class="text-white w-1/4 h-1/2 roboto fixed top-20 right-1/2 mr-10 z-0" v-html="selectedCharacter.name"></h1>
        <p v-if="selectedCharacter" class="text-[#7F7E7E] w-1/4 h-1/2 text-base roboto fixed top-30 right-1/2 mr-10 z-0" v-html="selectedCharacter.description"></p>
      </div>
    </div>

    <!-- Right -->
    <div class="right h-screen w-1/2 flex justify-center items-center flex-col">
      <!-- Section Title -->
      <div class="font-light mr-50 p-2.5 text-white roboto">
        <p class="opacity-0">CHARACTERS</p>
      </div>
      <!-- Grid -->
      <div class="grid grid-cols-2 w-1/2 gap-5 mt-10 ml-40 opacity-0 characters-wrapper">
        <div class="characters text-[#7F7E7E] text-sm hover:text-amber-300 cursor-pointer" 
        v-for="character in characters" 
        :key="character.name" 
        @click="selectCharacter(character)">
          {{ character.name }}
        </div>
      </div> 
    </div>

  </div>
</template>

<style>
</style>

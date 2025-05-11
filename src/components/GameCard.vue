<template>
  <a :href="game.link || '#'" class="bg-transparent hover:bg-[#1a1a1a] rounded-lg shadow-md hover:scale-[1.03] transition-transform snap-center w-[300px] flex-shrink-0 hover:border hover:border:solid hover:border-white">
    <div class="card__blocks">
      <!-- Image -->
      <div class="card__media-block">
        <img :src="game.image" :alt="game.title" class="rounded-lg w-full h-[300px] object-cover" />
      </div>

      <!-- Content -->
      <div class="p-4">
        <p class="text-xs uppercase text-blue-400 tracking-wide">Action</p>
        <h3 class="text-base font-bold my-1">{{ game.title }}</h3>
        <p class="text-sm text-gray-300">{{ game.description }}</p>

        <!-- Date -->
        <div class="flex items-center gap-1 text-xs text-gray-400 mt-3">
          <span>📅</span>
          <span>{{ game.date }}</span>
        </div>
      </div>
    </div>
  </a>
</template>

<script setup>
defineProps({
  game: Object
})
</script>

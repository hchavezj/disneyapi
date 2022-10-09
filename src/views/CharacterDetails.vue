<script setup>
import { onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'

import useCharacters from '@/composables/useCharacters'

const route = useRoute()
const { fetchCharacter, currentCharacter } = useCharacters()

onMounted(async () => {
  await fetchCharacter(route.params.id)
})

onUnmounted(() => {
  currentCharacter.value = null
})
</script>

<template>
  <main class="min-h-screen bg-slate-900 py-8 text-white">
    <div
      v-if="currentCharacter"
      class="flex flex-col items-center justify-center gap-6"
    >
      <img :src="currentCharacter.imageUrl" :alt="currentCharacter.name" />

      <h1 class="text-white-800 text-6xl font-bold">
        <p>Hi, I'm {{ currentCharacter.name }}</p>
        <p>I've appeared in</p>
      </h1>

      <div class="border p-5 pt-0">
        <ul v-if="currentCharacter.films.length" class="pt-3">
          <li>[ Films ]</li>
          <li v-for="films in currentCharacter.films" :key="films.id">
            {{ films }}
          </li>
        </ul>

        <ul v-if="currentCharacter.shortFilms.length" class="pt-3">
          <li>[ Short Films ]</li>
          <li
            v-for="shortFilms in currentCharacter.shortFilms"
            :key="shortFilms.id"
          >
            {{ shortFilms }}
          </li>
        </ul>

        <ul v-if="currentCharacter.tvShows.length" class="pt-3">
          <li>[ TV Shows ]</li>
          <li v-for="tvShows in currentCharacter.tvShows" :key="tvShows.id">
            {{ tvShows }}
          </li>
        </ul>
      </div>
      <!--<pre>{{ currentCharacter }}</pre>-->
    </div>
  </main>
</template>

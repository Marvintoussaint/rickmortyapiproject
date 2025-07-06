<script setup lang="ts">
// List of character variable
import type {Character} from "../types/Character.ts";
import {onMounted, ref} from "vue";
import axios from "axios";

const charList = ref<Character[]>([]);

onMounted(async () => {
  try {
    const response = await axios.get('https://rickandmortyapi.com/api/character');
    charList.value = response.data.results;
  }catch (err){
    console.log(err)
  }
})
</script>

<template>
  <div id="character-list" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 mt-8">
    <div
        v-for="character in charList"
        :key="character.id"
        class="max-w-sm rounded overflow-hidden shadow-lg bg-white"
    >
      <img class="w-full" :src="character.image" :alt="character.name" />
      <div class="px-6 py-4">
        <div class="font-bold text-xl mb-2">{{ character.name }}</div>
        <p class="text-gray-700 text-base">
          {{ character.status }}
        </p>
      </div>
      <div class="px-6 pt-4 pb-2">
        <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">Location : {{character.location.name}}</span>
        <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">Origin : {{character.origin.name}}</span>
        <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">Gender : {{character.gender}} </span>
      </div>
    </div>
  </div>
</template>


<style scoped>

</style>
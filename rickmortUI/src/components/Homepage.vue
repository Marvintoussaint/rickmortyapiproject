
<script setup lang="ts">


import CharacterList from "./CharacterList.vue";
</script>

<template>
  <div class="flex items-center justify-center mt-8">
    <input
        type="text"
        placeholder="Search characters..."
        class="w-full max-w-md px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
    />
    <button
        class="ml-2 px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700 transition"
    >
      Search
    </button>
  </div>
  <!--  character List-->
  <div id="character-component">
    <character-list/>
  </div>

</template>

<style scoped>

</style>
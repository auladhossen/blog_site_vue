<script setup>
import { onMounted, ref } from "vue";
import axios from "axios";
import { RouterLink } from "vue-router";

defineProps({
  menuOptions: Array,
});

const categories = ref([]);

list();

async function list() {
  let url = "https://basic-blog.teamrabbil.com/api/post-categories";
  let res = await axios.get(url);
  categories.value = res.data;
}
</script>

<template>
  <nav class="bg-white border-solid border-2 border-gray-200">
    <div class="mx-auto flex justify-between max-w-7xl px-2 sm:px-6 lg:px-8">
      <div class="flex items-center">
        <h1 class="text-gray-800 rounded-md px-3 py-2 text-sm font-medium">
          BLOG NEWS
        </h1>
      </div>

      <div class="flex gap-4 h-16 items-center justify-between">
        <div
          v-for="menu in categories"
          :key="menu.id"
          class="flex rounded-md px-1 py-2 hover:bg-blue-700 hover:text-white cursor-pointer sm:block font-bold text-xs items-center justify-center"
        >
          {{ menu.name }}
        </div>
      </div>
    </div>
  </nav>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>

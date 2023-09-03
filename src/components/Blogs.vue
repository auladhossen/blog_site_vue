<script setup>
import RecentPosts from "../components/RecentPosts.vue";
import axios from "axios";
import { ref } from "vue";

const postList = ref([]);

list();

async function list() {
  let url = "https://basic-blog.teamrabbil.com/api/post-list/2";
  let res = await axios.get(url);
  postList.value = res.data;
}
defineProps({
  posts: Array,
  newPosts: Array,
});
</script>

<template>
  <div class="flex px-9 py-6">
    <div>
      <div
        v-for="post in postList"
        :key="post.id"
        class="grid grid-cols-4 gap-4 my-3 border-2 rounded-md sm:ml-6 sm:block"
      >
        <div v-if="post">
          <img :src="post.img" class="rounded-t-lg" alt="post image" />
        </div>

        <div class="p-6">
          <div class="my-3 font-bold text-md">
            {{ post.title }}
          </div>
          <div class="text-sm">
            {{ post.short }}
          </div>
        </div>
      </div>
      <div
        v-for="post in postList"
        :key="post.id"
        class="grid grid-cols-4 gap-4 my-3 border-2 rounded-md sm:ml-6 sm:block"
      >
        <div v-if="post.img">
          <img :src="post.img" class="rounded-t-lg" alt="post image" />
        </div>

        <div class="p-6">
          <div class="my-3 font-bold text-md">
            {{ post.title }}
          </div>
          <div class="text-sm">
            {{ post.short }}
          </div>
        </div>
      </div>
    </div>
    <RecentPosts />
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>

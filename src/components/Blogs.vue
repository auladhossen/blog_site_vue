<script setup>
defineProps({
  posts: Array,
  newPosts: Array,
});
</script>

<template>
  <div class="px-9 py-6">
    <div class="text-center font-bold text-xl my-3">
      <h1>সাম্প্রতিক পোস্ট</h1>
    </div>

    <div
      v-for="post in newPosts"
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

    <div class="text-center font-bold text-xl my-3">
      <h1>সকল পোস্ট</h1>
    </div>

    <div
      v-for="post in posts"
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
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>

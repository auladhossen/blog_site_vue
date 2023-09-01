<script setup>
import { onMounted } from "vue";
import Navbar from "./components/Navbar.vue";
import Blogs from "./components/Blogs.vue";
import axios from "axios";

let menuOptions = [];
let posts = [];
let newPosts = [];

onMounted(() => {
  axios
    .get("https://basic-blog.teamrabbil.com/api/post-list/2")
    .then(function (response) {
      posts = response.data;
      console.log("blogPosts", posts);
    });

  axios
    .get("https://basic-blog.teamrabbil.com/api/post-categories")
    .then(function (response) {
      menuOptions = response.data;
      console.log("menuOptions", menuOptions);
    });

  axios
    .get("https://basic-blog.teamrabbil.com/api/post-newest")
    .then(function (response) {
      newPosts = response.data;
      console.log("newPosts", newPosts);
    });
});
</script>

<template>
  <Navbar :menuOptions="menuOptions" />
  <Blogs :posts="posts" :newPosts="newPosts" />
</template>

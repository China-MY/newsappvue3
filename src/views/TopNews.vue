<template>
  <div>
    <img src="../assets/logo.png" />
    <NewsList :data="newsList" v-if="newsList.length"></NewsList>
  </div>
</template>

<script setup>
import NewsList from "../components/NewsList.vue";
import { ref } from "vue";
import axios from "axios";

const newsList = ref([]);

function init() {
  axios
    .get("/juheNews?type=top&key=655962c80fdaccf03709b567da3bc795")
    .then(function (response) {
      newsList.value = response.data.result.data;
    })
    .catch(function (error) {
      console.log(error);
    });
}
init();
</script>

<style scoped>
img {
  width: 100%;
  height: 100px;
  display: block;
}
</style>
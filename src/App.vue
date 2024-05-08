<template>
  <div>
    <header>新闻头条</header>
    <nav>
      <ul>
        <li
          :class="{ navinit: isActive == 'topNews' }"
          @click="changeNav('topNews')"
        >
          头条新闻
        </li>
        <li
          :class="{ navinit: isActive == 'typeNews' }"
          @click="changeNav('typeNews')"
        >
          分类新闻
        </li>
      </ul>
    </nav>
    <router-view />
  </div>
</template>

<script setup>
import { useRouter } from "vue-router";
import { ref } from "vue";

const router = useRouter();

const isActive = ref("topNews");

const path = location.href.substring(location.href.lastIndexOf("/") + 1);
isActive.value = path == "" ? "topNews" : path;

function changeNav(param) {
  isActive.value = param;
  if (param == "topNews") {
    router.push("/topNews");
  } else if (param == "typeNews") {
    router.push("/typeNews");
  }
}
</script>


<style>
/**************** css reset *******************/
html,
body,
div,
header,
nav,
h1,
h2,
h3,
h4,
h5,
h6,
ul,
li {
  margin: 0;
  padding: 0;
  font-family: "微软雅黑";
}
ul {
  list-style: none;
}
a {
  text-decoration: none;
}

header {
  width: 100%;
  height: 48px;
  background-color: #e03d3e;

  display: flex;
  justify-content: center;
  align-items: center;

  font-size: 20px;
  color: #fff;
  letter-spacing: 4px;
}
nav {
  width: 100%;
  height: 56px;
  display: flex;
  justify-content: center;
  align-items: center;
}
nav ul {
  width: 160px;
  height: 26px;
  display: flex;
  justify-content: space-between;
}
nav ul li {
  width: 70px;
  height: 26px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.navinit {
  color: #e03d3e;
  border-bottom: solid 2px #e03d3e;
}
</style>

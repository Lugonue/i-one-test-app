<script setup>
import { ref } from "vue";

const randomComics = () => {
  return Math.floor(Math.random() * 2785);
};

const imgData = ref({});


const { data } = await useAsyncData("content", () =>
  $fetch(`https://xkcd.com/info.0.json`)
);
const dataInfo = ref(data.value);
imgData.value = data.value;
console.log(imgData.value.num, typeof imgData.value.num);
const currentPage = ref(`/${imgData.value.num}`);

const fetchData = async (arg) => {
  const index = currentPage.value.split("/")[1];
  switch (arg) {
    case "toStart":
      currentPage.value = "/1";
      break;
    case "randomContent":
      currentPage.value = `/${randomComics()}`;
      break;
    case "previous":
      if (index == 1) return;
      currentPage.value = `/${parseInt(index) - 1}`;
      break;
    case "next":
      if (index == dataInfo.value.num) return;
      currentPage.value = `/${parseInt(index) + 1}`;
      break;
    case "toEnd":
      currentPage.value = `/${dataInfo.value.num}`;
      break;
    default:
      break;
  }

  const url = `https://xkcd.com${currentPage.value}/info.0.json`;
  const { data } = await useAsyncData("content", () => $fetch(url));

  console.log(data.value);
  imgData.value = data.value;
};



</script>
<template>

  <div class="title">
    {{ imgData.title }}
  </div>
  <NavBar @get-content="fetchData" />
  <div class="content-container">
    <div class="widget" v-if="currentPage">
      {{ currentPage.slice(1) }} из {{ dataInfo.num }}
    </div>
    <img :src="imgData.img" :alt="imgData.title" />
  </div>
  <NavBar @get-content="fetchData" />

</template>

<style scoped>
.content-container {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 780px;
  height: 648px;
  background: #ffffff;
  margin: 45px 0;

  text-align: center;
}

img {
  width: auto;
  height: auto;
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
  margin: auto auto;
}

.title {
  width: auto;
  height: 26px;
  margin-bottom: 31px;
  font-size: 22px;
  color: #ffffff;
}

.widget {
  position: absolute;
  top: 0;
  right: 0;
  font-size: 0.5em;
  padding: 5px;
}
</style>

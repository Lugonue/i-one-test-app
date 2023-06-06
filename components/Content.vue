<script setup>

const randomComics = () => {
  return Math.floor(Math.random() * 2785);
};

let currentPage = ref("/1") ;
let imgData = ref({
  num: "",
  img: "",
  title: "",
}) ;

const fetchData = async (arg) => {
  console.log(arg, currentPage.value);
  const index = currentPage.value.split("/")[1];
  switch (arg) {
    case "toStart":
      currentPage.value = "/1";
      break;
    case "randomContent":
      currentPage.value = `/${randomComics()}`;
      break;
    case "previous":
      if (index === 1) return;
      currentPage.value = `/${Number(index) - 1}`;
      break;
    case "next":
      if (index === imgData.value.num) return;
      currentPage.value = `/${Number(index) + 1}`;
      break;
    case "toEnd":
      currentPage.value = `/${imgData.value.num}`;
      break;
    default:
      break;
  }

  const uri = 'https://xkcd.com' + currentPage.value + '/info.0.json';

  console.log(uri);

  const { data } = await useFetch(uri);

  console.log(data.value);

  imgData.value = data.value ?? imgData.value;
  return;
};

fetchData("toStart");

</script>
<template>
  <div class="title">
    {{ imgData.title }}
  </div>
  <NavBar @get-content="fetchData" />
  <div class="content-container">
    <div class="widget" v-if="currentPage">
      {{ currentPage.slice(1) }}
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

<script setup>
import { onMounted, ref } from 'vue';
import Image from './components/image.vue';
import Button from './components/button.vue';

const data = ref([]);
const images = ref ([]);

async function fetchData() {
  const result = await fetch('https://dog.ceo/api/breeds/list/all')
     .then(data => data.json())
     .then(response => Object.keys(response.message));

  return result;
}

async function fetchBreedData(name) {
   const result = await fetch(`https://dog.ceo/api/breed/${name}/images`)
     .then(data => data.json())
     .then(data => data.message);

     return result;
}

const selectHandler = async (breed) => {
  images.value = await fetchBreedData(breed);
 
}

onMounted (async () => {
  data.value= await fetchData();
  
})


</script>

<template>

<main class="main">
  <header class="header">
    <Image  v-for="image in images" :url="image"> </Image>
  </header>

  <content class="content">
    <Button  v-for="breed in data" @click="selectHandler(breed)"> </Button>
  </content>

</main>
</template>

<style scoped>

.main {
  width: 100%;
  min-height: 100vh;

  display: flex;
  flex-direction: column;
  align-items: stretch;
  justify-content: flex-start;
}

.header {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;

  min-height: 80px;

  background-color: pink; 
}

.content {
  margin: 40px;

  flex-grow: 1;
  flex-shrink: 1;
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: flex-start;
}

.affenpinscher {
  background-color: orchid;
}

.african {
  background-color: steelblue;
}
</style>

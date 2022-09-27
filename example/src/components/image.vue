<script setup>
const props = defineProps(['url']);
</script>

<template>
    <img :src="props.url"  >
    <br>
</template>

<style>
img {
  width: 200px;
  height: 200px;

  display: flex;
  flex-direction:initial;
  align-items: stretch;
  justify-content: flex-start;

}
</style>
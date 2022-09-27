<script setup>
    import { onMounted } from "vue";
    
    const props = defineProps(['name']);
    const emit = defineEmits(['setName']);
    
    const nameHandler = name => {
      emit('setName', name);
    }
    
    onMounted(() => console.log(`Button onMounted`));
    
    </script>
<template>
    <button class="button" @click="nameHandler(props.name)">{{ props.name }}</button>
</template>
<style scoped>
    .button {
  margin: 10px;
  padding: 12px 0;

  min-width: 120px;

  background-color: rgb(201, 145, 254);
  border: 2px solid rgb(37, 37, 37);
  cursor: pointer;
}

.affenpinscher {
  background-color: orchid;
}

.african {
  background-color: steelblue;
}

    </style>
<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <h1>Hello Vue!</h1>

  <button @click="count++">
    Count is: {{ count }}
  </button>
  
</template>

<style>
button {
  padding: 8px 16px;
  font-size: 18px;
  cursor: pointer;
}
</style>

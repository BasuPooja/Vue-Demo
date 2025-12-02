<!-- <script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <div>
    <h2>Counter application</h2>
    <h1>{{ count }}</h1>
    <button @click="count++">Increase</button>
  </div>
</template> -->


<template>
  <div>
    <h2>Counter application</h2>
    <h1>{{ count }}</h1>
    <button @click="count=0" style="margin-inline-start: 10px; height: 25px;">Reset</button>
    <button @click="count++" style="margin-inline-start: 10px; height: 25px;">Increase</button>

    <div style="margin-inline-start: 10px;" >
      <div v-if="count<1">
        <button disabled @click="count--" style="height: 25px;">Decrease</button>
      </div>
      <div v-else >
        <button @click="count--" style="height: 25px;">Decrease</button>
      </div>
    </div>
    
    
  </div>
</template>

 <script>
export default {
  data() {
    return {
      count: 0
    };
  }
};
</script>
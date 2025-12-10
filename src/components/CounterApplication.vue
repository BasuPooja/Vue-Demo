<template>
  <div class="container-div">
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

<style>

  .container-div {
  border: 2px solid black;
  width: 500px;
  height: auto;
  margin: auto;
  padding: 50px;
}
</style>
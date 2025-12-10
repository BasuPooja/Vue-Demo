<template>
  <div class="container-div">
    <h2>Counter application</h2>
    <h1>{{ count }}</h1>

    <button @click="count++" class="actionbtn" >Increase</button>
    <button :disabled = "count<1" @click="count--" class="actionbtn">Decrease</button>
    <button @click="count=0" class="actionbtn">Reset</button>
    
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

.actionbtn{
  margin-inline-start: 10px; 
  height: 25px;
    display: inline-flex;
  align-items: center;
  justify-content: center;
}
</style>
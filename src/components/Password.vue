<template>
<div class="container-div">
    <h2>Show/Hide Password</h2>

    <label>Select Method: </label>
    <select v-model="selectedMethod" style="height: 30px; margin-bottom: 15px;">
      <option value="v-if">v-if</option>
      <option value="v-show">v-show</option>
    </select>
    <br><br>
    <label for="password">Password: </label>
     <div v-if="selectedMethod === 'v-if'">
      <input style="height: 25px;" :type="showPassword ? 'text' : 'password'" v-model="password" placeholder="Enter password"/>
      <button @click="togglePassword"> {{ showPassword ? "Hide" : "Show" }}</button>
    </div>

    <div v-else>
     <input
      v-show="!showPassword"
      type="password"
      v-model="password"
      placeholder="Enter password"
      style="height: 25px;"
    />

    <input
      v-show="showPassword"
      type="text"
      v-model="password"
      placeholder="Enter password"
      style="height: 25px;"
    />
    <button @click="togglePassword"> {{ showPassword ? "Hide" : "Show" }}</button>
  </div>
    
</div>
</template>

<script>
  export default {
    data(){
      return{
        password: "",
        showPassword: false,
        selectedMethod: "v-if"
        
      };
    },
    methods: {
      togglePassword(){
        this.showPassword =! this.showPassword;
      }
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
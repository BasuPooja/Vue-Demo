<template>
    <div class="container-div">
        <h2>Live Character Count</h2>
        <textarea v-model = "texInput" placeholder = "Type somethings....." rows="4" cols="40" class="textbox"></textarea>
        <p :style = "{ color: charCount > 50 ? 'red' : 'black' }"> characters: {{ charCount }} </p>
    </div>
</template>
<script>
    export default{
        data(){
            return{
                texInput: ""
            };
        },
        computed: {
            charCount(){
                return this.texInput.length;
            }
        }
    }

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
<template>
  <div>
    <h1>All Task at same compnent</h1>
    <br>
    <button @click="task = 'CounterApplication'" class="hbtn">Counter </button>

    <button @click="task = 'TodoList'" class="hbtn" >TodoList </button>
    <br>
    <br>
    <component :is = "task"></component>
  </div>
</template>
<script>
import CounterApplication from './components/CounterApplication.vue';
import TodoList from './components/TodoList.vue';

export default{
  data(){
    return{
      task: "CounterApplication"
    };
  },
  components:{
    CounterApplication,
    TodoList
  }
};
</script>

<style>
.hbtn{
  margin-inline-start: 10px; 
  height: 35px; 
  background-color:rgb(78, 226, 226);
  
  font-weight: bold;
  font-size: 20px;
}
</style> -->
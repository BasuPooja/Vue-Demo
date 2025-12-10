<template>
  <div>
    <h1>All Task at same compnent</h1>
    <br>
    <button @click="task = 'CounterApplication'" class="hbtn">Counter </button>

    <button @click="task = 'TodoList'" class="hbtn" >TodoList </button>

    <button @click="task = 'Password'" class="hbtn" >Password </button>

    <button @click="task = 'LivecharacterCount'" class="hbtn" >Live Character Counter</button>
    
    <button @click="task = 'RealTimeSearch'" class="hbtn" >Real Time Search Filter</button>
    <br>
    
    <br>
    <component :is = "task"></component>
  </div>
</template>
<script>
import CounterApplication from './components/CounterApplication.vue';
import Password from './components/Password.vue';
import TodoList from './components/TodoList.vue';
import LivecharacterCount from './components/LivecharacterCount.vue';
import RealTimeSearch from './components/RealTimeSearch.vue';

export default{
  data(){
    return{
      task: "TodoList"
    };
  },
  components:{
    CounterApplication,
    TodoList,
    Password,
    LivecharacterCount,
    RealTimeSearch
  }
};
</script>

<style>

.hbtn{
  margin-inline-start: 10px; 
  height: 35px; 
  background-color:rgba(3, 88, 88, 0.445);
  font-size: 18px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

</style> 
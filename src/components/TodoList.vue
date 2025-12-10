<template>
    <div class="container-div">
    
    <h1>ToDoList</h1>
    <div style="display: inline-flex;">
      <input @keyup.enter="AddTask" class="inputbox" type="text"  placeholder = "Enter task" v-model="newTask">
      <button class="add" style="background-color: #4CAF50;" @click="AddTask"><i class="fa fa-plus"></i>Add</button>
    </div>

    <!-- <ul>
        <tasklist
        v-for="(task, index) in tasks"
        :key="index"
        :tasks="task"
        @edit = "editTask(index)"
        @remove = "removeTask(index)"
        />
    </ul> -->

    <h2>Real Time Search Filter</h2>

    <input type="text" v-model="searchText" placeholder="Search items..." class="inputbox"/>
    <div class="table-container">
      <div class="table-header">
        <div class="table-cell">Checklist</div>
        <div class="table-cell">Tasks</div>
        <div class="table-cell">Action</div>
        <div class="table-cell">Action</div>
      </div>
      <div class="table-row" v-for="(task, index) in searchlist" :key="index">
        <div class="table-cell">
          <input type="checkbox" v-model="task.completed" />
        </div>

        <div class="table-cell">
          <span v-if="!task.editing">
            <span :style="{textDecoration: task.completed ? 'line-through' : 'none'}">
              {{ task.name }}
            </span>
          </span>

          <input
            v-else
            type="text"
            v-model="task.name"
            @keyup.enter="saveEdit(index)"
          />
        </div>

        <div class="table-cell">
          <button @click="editTask(index)" class="edit-btn">
            {{ task.editing ? "Save" : "Edit" }}
          </button>
        </div>

        <div class="table-cell">
          <button @click="removeTask(index)" class="delete-btn">
            Delete
          </button>
        </div>
      </div>
      
    </div>
<br>
    <div style="display: inline-flex;">
      <button @click="ClearItem" class="clear" >Clear all</button>
      <button @click="ClearcompleteItem" class="allclear">Clear completed</button>
    </div>
    
    
    </div>
</template>

<script>

import tasklist from "./tasklist.vue";

export default{
  components:{tasklist,},
  name:"App",
  data(){
    return{
        newTask: "",
        tasks: [],
        searchText:"",
    };
  },

  computed: {
            searchlist() {
              return this.tasks.filter((item) =>
                item.name.toLowerCase().includes(this.searchText.toLowerCase())
              );
            },
        },

  methods:{
    AddTask(){
        if(this.newTask.trim()=="")
            return;
        this.tasks.push({
        name: this.newTask,
        completed: false,
        editing: false,
      });
        this.newTask = "";

    },
    removeTask(index){
        this.tasks.splice(index,1);
    },

    editTask(index) {
      this.tasks[index].editing = !this.tasks[index].editing;
    },

    saveEdit(index) {
      this.tasks[index].editing = false;
    },

    ClearItem() {
      this.tasks = [];
    },

    ClearcompleteItem() {
      this.tasks = this.tasks.filter((t) => !t.completed);
    },
  },
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

.inputbox {
  margin-left: 10px;
  height: 25px;
  width: 300px;
  margin: 10px;
}

.add {
  height: 30px;
  width: 100px;
  font-size: medium;
  font-weight: bold;
  margin: auto;
  display: inline-flex;
}

/* TABLE */
.table-container {
  border: 1px solid #ccc;
  border-radius: 5px;
  overflow: hidden;
  margin-top: 20px;
}

.table-header,
.table-row {
  display: flex;
}

.table-header {
  background-color: #f0f0f0;
  padding: 10px;
}

.table-row {
  border-top: 1px solid #ddd;
  padding: 10px;
}

.table-cell {
  flex: 1;
  padding: 5px;
  font-size: 16px;
}

.edit-btn {
  background: rgb(182, 255, 122);
  padding: 5px 10px;
  border: none;
  cursor: pointer;
  font-weight: bold;
}

.delete-btn {
  background: rgb(255, 90, 90);
  padding: 5px 10px;
  color: white;
  border: none;
  cursor: pointer;
  font-weight: bold;
}

.clear,
.allclear {
  height: 40px;
  font-size: medium;
  font-weight: bold;
  margin: 10px;
  display: inline-flex;
}

.clear {
  width: 100px;
  background-color: red;
}

.allclear {
  width: 150px;
  background-color: orange;
}
</style>
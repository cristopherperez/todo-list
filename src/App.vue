<template>
  <div>
    <div>
      <input type="text" v-model="newTaskName" />
      <button @click="addTask">+</button>
    </div>
    <task-list 
    title="Tareas pendientes" 
    :list="todoTask" 
    @change-task-status="changeTaskState"/> 
    <task-list 
    title="Tareas listas" 
    :list="doneTask" 
    @change-task-status="changeTaskState"/> 
  </div>
</template>

<script>
import TaskList from "./components/TaskList";

export default {
  name: "App",
  components: {
    TaskList,
  },
  data(){
    return{
      newTaskName: "",
      tasks:[]
    };
  },
  computed:{
    doneTask(){
      return this.tasks.filter(task=> task.done);
    },
    todoTask(){
      return this.tasks.filter(task => !task.done);
    },
  },
  methods:{
    addTask(){
      const newTask = {
        name: this.newTaskName,
        done: false
      };
      this.tasks.push(newTask);
      this.newTaskName = "";
    },
    changeTaskState(task){
      const idx = this.tasks.indexOf(task);
      this.tasks[idx].done = !this.tasks[idx].done
    },
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

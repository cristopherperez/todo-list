<template>
  <div>
      <h4>{{ title }}</h4>
      <task
      v-for="task in list" 
      :key="`task-${task.name}`" 
      :taskName="task.name" 
      :checked="task.done" 
      @change-check="changeTaskStatus(task)" />
  </div>
</template>

<script>
import Task from './Task';

export default {
    name: 'TaskList',
    components: { 
        Task 
    },
    props:['title', 'list'],
    methods:{
        changeTaskStatus(task){
            this.$emit("change-task-status", task);
        }
    }
};
</script>

<style>

</style>
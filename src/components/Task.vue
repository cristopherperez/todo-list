<template>
  <div>
      <span>{{ taskName }}</span>
      <input type="checkbox" :checked="checked" @change="emitChange"/>
  </div>
</template>

<script>
export default {
    name: 'Task',
    props: ['taskName', 'checked'],
    methods:{
        emitChange (){
            this.$emit('change-check');
        }
    }
};
</script>

<style>

</style>
<template>
  <header>
    <h1>{{title}}</h1>
    <ButtonVue :text="showAddTask ? 'Close' : 'Add Task'" @toggle-add-task="$emit('toggle-add-task')" :color="showAddTask ? 'red' : 'green'"/>
    <!-- <ButtonVue text="Update Task" color="blue"/> -->
    <!-- <ButtonVue text="Delete Task" color="red"/> -->
  </header>
</template>

<script>
import ButtonVue from './Button.vue';

export default {
  name: "HeaderVue",
  // props: ['title']
  props: {
    title: String,
    showAddTask: Boolean
  },
  components: {
    ButtonVue
  }
}
</script>


<style scope> 
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>
    <!-- when we add 'scope' to the style tag, it limites the styling to just the elements in this component -->

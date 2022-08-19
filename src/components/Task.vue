<template>  
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']"> <!-- in addition to the 'task' class, this is a ternary operator to add another 'reminder' class-->
        <h3>{{task.text}}<i @click="onDelete(task.id)" class="fas fa-times"></i></h3> <!-- we added a link tag on line 7 in index.html to get this icon -->
        <p>{{task.day}}</p>
    </div>
</template>

<script>
export default {
  name: "TaskVue",
  props: {
    task: Object
  },
  methods: {
    onDelete(id) {
        // console.log(id)
        // this is how we execute events to call funcs in parent components with an argument coming from here
        this.$emit('delete-task', id)
        // this defines a new prop event thing called '@delete-task' on this component in the parent component... 
        // ...where we can call a function defined in it (with this 'ID' argument), or repeat the process upwards to call a func in a higher component
    }
  }
};
</script>

<style scope>
.fas {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
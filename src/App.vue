<template>
  <div class="container">
    <HeaderVue title='Task Tracker' @toggle-add-task="toggleAddTask" :showAddTask="showAddTask"/> <!-- we're making a showAddTask prop, and passing in the boolean value of whatever the showAddTask variable is-->
    <div v-if="showAddTask">
      <AddTask @add-task='addTask'/>
    </div>
    <TasksVue @delete-task="deleteTask" @toggle-reminder='toggleReminder' :tasks="tasks" />    
  </div>
</template>

<script>
import HeaderVue from './components/Header.vue'
import TasksVue from './components/Tasks.vue'
import AddTask from './components/AddTask.vue';

export default {
  name: "App",
  components: {
    // we must define any components that we import into our main App component here
    HeaderVue,
    TasksVue,
    AddTask
},
  data() {
    return {
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      // console.log('Deleting task: ', id)
      // if (confirm('Are you sure?')) {
        this.tasks = this.tasks.filter(task => task.id !== id)
      // }
    },
    toggleReminder(id) {
      // console.log('Toggle reminder: id)
      this.tasks = this.tasks.map(task => task.id == id ? {...task, reminder: !task.reminder} : task)
      // we go through each object in the list, if the current task.id matches the argument id...
      // ...we use the spread operator syntax to update the reminder property in that object and return it, otherwise...
      // ...we just return the same unaltered list
    },
    toggleAddTask () {
      this.showAddTask = !this.showAddTask
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Doctors Appointment',
        day: 'March 1st at 2:30pm',
        reminder: true
      },
      {
        id: 2,
        text: 'Meeting at School',
        day: 'March 3rd at 1:30pm',
        reminder: true
      },
      {
        id: 3,
        text: 'Food Shopping',
        day: 'March 3rd at 11:00am',
        reminder: false
      }
    ]
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>

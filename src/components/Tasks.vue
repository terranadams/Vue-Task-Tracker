<template>
    <div :key="task.id" v-for="task in tasks">
        <TaskVue @delete-task="$emit('delete-task', task.id)" :task="task"/>
    </div>
</template>

<script>
import TaskVue from './Task.vue';
export default {
    name: 'TasksVue',
    props: {
        tasks: Array
    },
    components: {
        TaskVue
    },
    emits: ['delete-task'] // this is just to get rid of the warning in the console really
}
</script>
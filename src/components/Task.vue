<template>
    <div :key="task.id" v-for="task in tasks">
        <IndvTask @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" :task="task"/>
    </div>
</template>
 

<script>
import IndvTask from './IndvTask.vue'

    export default{
        name: 'Tasks',
        props: {
            tasks: Array
        },
        components:{
            IndvTask
        },
        emits:['delete-task', 'toggle-reminder']
    }
</script> 
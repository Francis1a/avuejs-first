<template>
    <section @dblclick="$emit('toggle-reminder', id)" :class="[task.reminder? 'reminder' : '','task']">
        <h3 class="prevent-select">{{ task.text }}
        <i @click="$emit('delete-task', id)" class="fas fa-times"></i>
        </h3>
        <p class="prevent-select">{{ task.day }}</p>
    </section>
</template>

<script>
    export default{
        name: 'IndvTask',
        props:{
            task: Object,
        },
    }
</script>

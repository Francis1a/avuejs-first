<template>
    <button @click="onClick()" :style="{background: color}">{{ text }}</button>
</template>

<script>
    export default{
        name: 'Button',
        props: {
            text: String,
            color: String,
        },
        methods:{
            onClick(){
                console.log('click')
                this.$emit('toggleBtnAddTask')
            },
        },
    }
</script>

<style scoped>
button{color: #fff; width: 100px;}
</style>
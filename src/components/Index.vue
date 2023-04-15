<template>

      <div class="box">
        <h1 class="prevent-select">Task Manager</h1>
       <Button @toggleBtnAddTask = "$emit('toggleBtnAddTask')" :text="showAddTask ? 'Close' : 'Add Task'" :color="showAddTask ? 'red' : 'green'"/> 
      </div>
</template>

<script>
import { booleanLiteral } from '@babel/types';
import Button from './Button'

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    showAddTask: Boolean,
  },
  components:{
    Button
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box{display: flex; justify-content: space-evenly; align-items: center;}
</style>

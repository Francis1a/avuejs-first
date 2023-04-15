<template>
    <div class="container">
      <Index :showAddTask="showAddTask"  @toggleBtnAddTask='showFormTask'/>
      <div v-show="showAddTask">
        <AddTask @add-task="addTask"/>
      </div>
      <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
    </div>
</template>

<script>
import Index from './components/Index'
import Tasks from './components/Task'
import AddTask from './components/AddTask'

export default {
  name: 'App',
  props: {
    showAddTask: Boolean,
  },
  components: {
    Index,
    Tasks,
    AddTask
  },
  emits:['deleteTask'],
  data() {
    return{
      tasks: [],
      showAddTask: false,
    }
  },

  methods:{
    showFormTask(){
      this.showAddTask = !this.showAddTask
    },
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id){
      console.log('task',id)
      if (confirm('Are you sure?')){
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },

    toggleReminder(id){
      console.log('task',id);
      this.tasks =  this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: ' Doctors Appointment',
        day: 'April 1, 2301',
        reminder: false,
      },
      {
        id: 2,
        text: 'Meeting on Sm',
        day: 'March 1, 0301',
        reminder: true,
      },
      {
        id: 3,
        text: 'Dental Appointmen',
        day: 'January 5, 2321',
        reminder: true,
      },
      {
        id: 4,
        text: 'Gym Time',
        day: 'April 1, 23044',
        reminder: false,
      }
    ]
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.reminder.task{border-left: 10px solid #8ec68e}
button {   height: fit-content;   padding: 10px;   border: none;   border-radius: 5px;   background: #cccc; }
button:hover {   background: #000;   color: #fff;   transition: all .5s ease-in-out;cursor: pointer; }
.container {   max-width: 480px;   margin: auto;   border: 2px solid #dfdfdf;   border-radius: 11px;min-height: 200px;  padding: 10px;background: #e6e6e6; }
.container section {   text-align: left;   padding: 1px 20px;   background: #d7d7d7;   margin-bottom: 10px; position: relative; border-radius: 10px;}
h3 i {   position: absolute;   right: 10px;   top: 10px; z-index: 9;}
.container section {   cursor: pointer; }
.prevent-select {
  -webkit-user-select: none; /* Safari */
  -ms-user-select: none; /* IE 10 and IE 11 */
  user-select: none; /* Standard syntax */
}
</style>S

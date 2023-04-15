<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Task</label>
            <input type="text" v-model="text" name="text" placeholder="Add Task" />
        </div>
        <div class="form-control">
            <label>Day & Time</label>
            <input type="text" v-model="day" name="day" placeholder="Add Day & Time" />
        </div>
        <div class="form-control form-control-check">
            <label>Set Reminder</label>
            <input type="checkbox" v-model="reminder" name="reminder" />
        </div>

        <input type="submit" value="Save Task" class="btn btn-block" />
    </form>
</template>

<script>
    export default{
        name: 'AddTask',
        data(){
            return {
                text: '',
                day: '',
                reminder: false
            }
        },
        methods:{
            onSubmit(e){
                e.preventDefault()

                if(!this.text){
                    alert('Please add a task')
                    return
                }
                const newTask = {
                    id: Math.floor(Math.random() * 100000),
                    text: this.text,
                    day: this.day,
                    reminder: this.reminder,
                }

                console.log(newTask),

                this.$emit('add-task', newTask)

                this.text = ''
                this.day = ''
                this.reminder = false
            }
        }
    }
</script>

<style scoped>
.add-form {   margin: 20px; }
.form-control {   display: flex;   justify-content: space-between;margin-bottom: 0.7em; align-items: center; min-height: 38px;}
label {   display: inline;   font-size: 1.17em;   font-weight: bold;   margin-block-start: unset;   margin-block-end: unset;   text-align: left; }
input[type="text"] {   max-width: 100%; width: 270px;   border-radius: 5px;   border: 0.5px solid #bbb8b8; padding: 10px;}
input[type="checkbox"] {   margin: auto auto auto 30px; }
.btn.btn-block {   cursor: pointer;   border: 1px solid #fff;   background: rgb(47,53,129);   background: linear-gradient(22deg, rgb(47, 53, 129) 0%, rgb(78, 18, 107) 100%);   color: #fff;   padding: 10px 40px;   border-radius: 11px;   font-size: 19px;   box-shadow: 5px 5px 15px -4px #4f4f4f; }
</style>

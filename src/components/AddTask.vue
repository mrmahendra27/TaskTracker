<template>
    <form @submit="saveTask" class="add-form">
        <div class="form-control">
            <label>Task</label>
            <input type="text" name="text" v-model="text" placeholder="Add Task">    
        </div>
        <div class="form-control">
            <label>Add Date and Time</label>
            <input type="text" name="day" v-model="day" placeholder="Add Day and Time">    
        </div>
        <div class="form-control-check">
            <label>Set Reminder</label>
            <input type="checkbox" name="reminder" v-model="reminder">    
        </div>
        <input type="submit" value="Save Task" class="btn btn-block">
    </form>    
</template>

<script>
export default {
    name: 'AddTask',
    data() {
        return {
            text: '',
            day: '',
            reminder: false
        }
    },
    methods: {
        saveTask(e){
            e.preventDefault()

            if(!this.text){
                alert('Please add a task!!!')
                return
            }

            if(!this.day){
                alert('Please add day!!!')
                return
            }

            const addTask = {
                // id: Math.floor(Math.random() * 10000),
                text: this.text,
                day: this.day,
                reminder: this.reminder,    
            }

            this.$emit('save-task', addTask)
            this.text = ''
            this.day = ''
            this.reminder = false
        }
    },
}
</script>

<style scoped>
.add-form{
    margin-bottom: 50px;
}
.form-control {
    margin: 20px 0px;
}

.form-control label {
    display: block;
}

.form-control input {
    height: 40px;
    width: 100%;
    margin: 5px;
    padding: 3px 7px;
    font-size: 15px;
}

.form-control-check {
    margin: 20px 0px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.form-control-check label {
    flex: 1;
}

.form-control-check input {
    flex: 2;
    height: 15px;
}
</style>
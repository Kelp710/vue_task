<template>
<form @submit="onSubmit">
    <div>
        <label>task</label>
        <input v-model="text" placeholder="add anything" name="text" />
    </div>
    <div>
        <label>day</label>
        <input v-model="day" placeholder="add anything2" name="day"/>
    </div>
    <div>
        <label>reminder</label>
        <input v-model="reminder" type="checkbox" name="reminder"/>
    </div>
    <input type="submit" />
</form>
</template>

<script>
export default{
    name: 'AddTask',
    data(){
        return {
            text:"",
            day:"",
            reminder: false
        }
    },
    methods:{
        onSubmit(e){
            e.preventDefault()

            if(!this.text){
                alert("add your task")
                return
            }

            const newTask = {
                id: Math.floor(Math.random() * 100000),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }
            this.$emit('add-task', newTask)

            this.text="",
            this.day="",
            this.reminder= false
        }
    }
}
</script>
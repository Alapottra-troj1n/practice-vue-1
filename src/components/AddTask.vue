<template>
    <form @submit="handleSubmit" >
        <div>
            <label for="title">Title</label>
            <input type="text" v-model="title" name="title" id="title" />
        </div>
        <button type="submit">Add Task</button>
    </form>
</template>

<script>
export default {
    name: 'AddTask',
    data() {

        return {
            title: '',
            completed: false,
        }

    },
    
    methods: {
        handleSubmit(e){
            e.preventDefault();
            if(!this.title){
               return alert('Empty Input')
            }

            const newTask = {
                id: Math.floor(Math.random() * 100000),
                title: this.title,
                completed: this.completed,

            }

           this.$emit('add-task', newTask)

            this.title = ''


        }
    }

}
</script>

<style scoped>

</style>
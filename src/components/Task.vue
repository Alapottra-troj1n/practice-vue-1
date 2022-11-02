<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.completed ? 'reminder' : '', 'task']" >
                <h2>{{task.title}}</h2>
                <h2>Complete : {{task.completed}}</h2>
                <button @click="onDelete(task.id)" >X</button>
    </div>
</template>

<script>
    export default {
        name: 'Task',
        props: {
            task: Object
        },
        methods: {
            onDelete(id){
               
                this.$emit('delete-task',id)
            }
        }
    }
</script>

<style scoped>
        div{
            padding: 20px 20px;
            background-color: rgba(136, 136, 136, 0.241);
            margin: 10px 0;
        }
        .reminder{
            border-left: 21px solid rgb(17, 238, 17);
        }
</style>
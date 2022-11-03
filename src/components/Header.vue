<template>
    <header>
        <h2>{{title}}</h2>
        <Button @toggle-task-btn="$emit('toggle-task-btn')" :title="showTask ? 'Close' : 'Add Task' "  />
    </header>
</template>

<script>
import Button from './Button.vue';


export default {
    name: "Header",
    props: { 
        title: String,
        showTask: Boolean
            
    }
    ,
    components: { Button }
}

</script>









<style scope>

header{
    display: flex;
    justify-content: center;
    width: 70vw;
    margin: 0 auto;
    justify-content: space-around;
}

</style>
<template>
    <button @click="$emit('toggle-task-btn')" >
        {{title}}
    </button>
</template>

<script>
    export default {
        name: 'Button',
        props: {
            title: String
        }


    }
</script>

<style scoped>
        button{
            padding: 10px 25px;
            background-color:black;
            color:white;
            cursor: pointer;

        }
</style>
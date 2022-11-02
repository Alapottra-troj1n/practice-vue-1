<template>
    <header>
        <h2>{{title}}</h2>
        <Button/>
    </header>
</template>

<script>
import Button from './Button.vue';


export default {
    name: "Header",
    props: { title: {
            Type: String
        }, component: { Button }
    },
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
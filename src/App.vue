<script>
import AddTask from './components/AddTask.vue';
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue'

export default {
  name: 'App',
  components: { Header, Tasks, AddTask },

  data() {
    return {
      tasks: []
    }
  },
  
  methods: {
      deleteTask(id){
        if(confirm("Are you sure")){
          this.tasks  = this.tasks.filter((task) => task.id !== id  )
        }
      },

      toggleReminder(id){
        this.tasks = this.tasks.map(task => task.id === id ? {...task, completed: !task.completed} : task  )
      },
      addTask(newTask){

        this.tasks = [...this.tasks, newTask];

      }

  },


  created() {
    this.tasks = [
      {
        "userId": 1,
        "id": 1,
        "title": "delectus aut autem",
        "completed": true
      },
      {
        "userId": 1,
        "id": 2,
        "title": "quis ut nam facilis et officia qui",
        "completed": false
      },
      {
        "userId": 1,
        "id": 3,
        "title": "fugiat veniam minus",
        "completed": false
      }
    ]
  },




}



</script>

<template>
  <Header title="Test Application" />
  <AddTask @add-task="addTask" />
  <h2>Hello World</h2>
  <Tasks @toggle-reminder="toggleReminder"  @delete-task="deleteTask" :tasks="tasks" />



</template>


<style scoped>
h2 {
  text-align: center;
}
</style>

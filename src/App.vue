<script>
import AddTask from './components/AddTask.vue';
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue'

export default {
  name: 'App',
  components: { Header, Tasks, AddTask },

  data() {
    return {
      tasks: [],
      showTask: false,
      posts : []
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

      },
      toggleTask(){

        this.showTask = !this.showTask;

      },
      async fetchPost(){
        const res = await fetch('https://jsonplaceholder.typicode.com/posts');
        const data = res.json();
        return data;

      }

  },


  async created() {

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
    ],
    this.posts = await this.fetchPost();

    
  },





}



</script>

<template>
  <Header :showTask="showTask" @toggle-task-btn="toggleTask" title="Test Application" />
  <div v-show="showTask" ><AddTask @add-task="addTask" /></div>
  <h2>Hello World</h2>
  <Tasks @toggle-reminder="toggleReminder"  @delete-task="deleteTask" :tasks="tasks" />

<div>
  <h2>Fetched From API</h2>
  <div v-for="post in posts" >
      {{post.title}}
  </div>
</div>



</template>


<style scoped>
h2 {
  text-align: center;
}
</style>

<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <form v-on:submit="addTask">
      <input v-model="taskUser">
      <input type="submit">
    </form>
    <div v-if="tasks !== null">
      <ul v-for="task in tasks" v-bind:key="task.id"> 
        <Task 
          v-bind:title="task.title"
          v-bind:completed="task.completed"
          v-bind:id="task.id"
          ></Task>     
      </ul>
    </div>
    <div v-else>
      Loading...
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue';
import Task from './components/Task';
import axios from 'axios'
import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'App',
  components: {
    Task
  },
  data () {
    return {
      tasks: null,
      taskUser: '',
      }
  },
  mounted () {
    axios
      .get('https://jsonplaceholder.typicode.com/todos')
      .then(response => (this.tasks = response.data))
  },
  methods: {
    addTask: function(event) {
      this.tasks.push({ id: uuidv4(), title: this.taskUser, completed: false });
      this.taskUser = ''
      event.preventDefault();
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.completed {
  color: black;
  text-decoration: line-through;
}
.completed-svg {
  width:20px;
}
.notCompleted {
  color: black;
}
.notCompleted-svg {
  width: 20px;
}
.delete-svg {
  width: 20px;
}
</style>

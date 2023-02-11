<template>
  <div id="app">
    <h1>TODO LIST</h1>
    <form @submit.prevent="addTodo">
      <input type="text" v-model="text" />
      <button>Add Todo</button> 
    </form>

    <p>List of Todos</p>
    <ul>
      <li v-for='todo in todoArray'>
        <input type="checkbox" v-model="todo.check">
        <span  v-bind:class="{ 'done': todo.check }">{{todo.name}}</span>
        <button @click="deleteTodo(todo)">delete</button>
      </li>
    <ul>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  data() {
    return {
      text: '',
      todoArray: [],
    };
  },
  methods: {
    addTodo() {
      if(this.text === '') {
        return
      }
      this.todoArray.push({name: this.text, done: false});
      this.text = ''
    },
    deleteTodo(todo){
      console.log(todo)
         const index = this.todoArray.indexOf(todo);
          this.todoArray.splice(index, 1);
    }
    
  },
};
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
ul {
  list-style: none;
}
.done{
  text-decoration: line-through;
}
</style>

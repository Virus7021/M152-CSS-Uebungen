<template>
  <div>
    {{ test }}
    <br>
    <input type="text" v-model="test"/>
  </div>
  <div>
    <h1> {{ todoCount }} Aufgaben ({{ totalTime }} Min)</h1>
    <ul>
      <li v-for="todo in todos">{{ todo.name }} ({{ todo.time }} Min)</li>
    </ul>
    <input placeholder="name" v-model="newTodo">
    <input placeholder="time" v-model="newTime">
    <button v-on:click="addTodo">Add todo</button>
  </div>
</template>

<script>
  export default {
    name: 'App',
    data: function() {
      return {
        test: "Hello World!!!!!!!!",
        newTodo: "",
        newTime: 0,
        todos: [
          {
            name: "something",
            time: 10
          },
          {
            name: "something else",
            time: 15
          }
        ]
      }
    },
    methods: {
      addTodo: function() {
        if(this.newTodo != '' && this.newTime >= 0) {
          this.todos.push({name: this.newTodo, time: parseInt(this.newTime)})
          this.newTodo = ''
          this.newTime = 0
        }
      }
    },
    computed: {
      todoCount: function() {
        return this.todos.length
      },
      totalTime: function() {
        var time = 0;
        for (var todo of this.todos) {
          time += parseInt(todo.time)
        }
        return time
      }
    }
  }
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>

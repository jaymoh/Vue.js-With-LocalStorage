<template>
  <div id="app" class="card center_div">
    <div class="sticky-top bg-light">
      <Header></Header>
      <AddTodoItem v-on:add-todo-event="addTodoMethod"></AddTodoItem>
    </div>
    <div class="overflow-auto">
      <Todos v-bind:todo_items="todo_items"/>
    </div>
  </div>
</template>

<script>
    import Header from './components/Header.vue';
  import AddTodoItem from './components/AddTodoItem.vue'
  import Todos from './components/Todos.vue'

export default {
  name: 'app',
  components: {
      Header,
      Todos,
      AddTodoItem
  },
    data() {
      return {
          todo_items : []
      }
    },
    methods: {
        addTodoMethod(newTodoItem){
            this.todo_items = [...this.todo_items, newTodoItem]
      }
    },
    mounted(){
      console.log('App Mounted');
        if (localStorage.getItem('todo_items'))
            this.todo_items = JSON.parse(localStorage.getItem('todo_items'));
    },
    watch: {
        todo_items: {
            handler() {
                console.log('Todo Items array changed!');
                localStorage.setItem('todo_items', JSON.stringify(this.todo_items));
            },
            deep: true,
        },
    },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 50px;
}
.center_div{
  margin: 0 auto;
  width: 80%
}
</style>

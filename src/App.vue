<template>
  <div>
    Task2 <br>
    <MyButton v-on:added="addIsCalled()" state="add"></MyButton>
    <MyButton v-on:deleted="deleteIsCalled()" state="delete"></MyButton>
    <br>
    <br>

    Task3 <br/>
    <TodoItem v-on:marked-as-pending="pendingIsCalled()" v-on:marked-as-done="doneIsCalled()" :todo="todo"></TodoItem>
    <TodoItem v-on:marked-as-pending="pendingIsCalled()" v-on:marked-as-done="doneIsCalled()" :todo="todo1"></TodoItem>
    <br>

    Task4 <br/>
    <TodoItem 
      @todo-deleted="deleteTodo"
      :key="todoItem.id" 
      v-for="todoItem in taskList" 
      :todo="todoItem">
    </TodoItem>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue';

export default {
  name: 'App',
  data() {
    return {
      taskList: [
        {
          id: 1,
          task: "Work",
          state: "pending"
        },
        {
          id: 2,
          task: "Study",
          state: "pending"
        },
        {
          id: 3,
          task: "Play",
          state: "pending"
        },
        {
          id: 4,
          task: "Run",
          state: "pending"
        }
      ],
      todo: {
        task: "hello",
        state: "done"
      },
      todo1: {
        task: "hello1",
        state: "pending"
      }
    }
  },
  components: {
    TodoItem
  },
  methods: {
    addIsCalled() {
      console.log('added');
    },
    deleteIsCalled() {
      console.log('deleted');
    },
    pendingIsCalled() {
      console.log("pending");
    },
    doneIsCalled() {
      console.log("done");
    }
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
</style>

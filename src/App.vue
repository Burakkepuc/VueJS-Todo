<template>
  <div class="container">
    <Header title="Todo App" />
    <Form @add-task="addTask" />
    <Tasks @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Form from './components/Form.vue';
import Tasks from './components/Tasks.vue';
export default {
  name: 'App',
  components: {Header, Form, Tasks},
  data() {
    return {
      tasks: [],
    };
  },

  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id);
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        task: 'Do your Homework',
        description: 'Math lecture',
      },
      {
        id: 2,
        task: 'Go to gym',
        description: 'Chest day',
      },
      {
        id: 3,
        task: 'Meet with your friends',
        description: 'Go to coffee shop',
      },
    ];
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Roboto', sans-serif;

  font-size: 12px;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
</style>

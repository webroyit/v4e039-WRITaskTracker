<template>
  <div class="container">
    <Header title="WRI Task Tracker" />
    <AddTask @add-task="addTask" />
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from './components/Header';
import Tasks from './components/Tasks';
import AddTask from './components/AddTask';

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: []
    }
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      if (confirm('Are you sure?')){
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    }
  },
  // This is a life cycle method
  // Commonly use for making http requests or load data
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Water the plant',
        day: 'April 12 at 1:00pm',
        reminder: true
      },
      {
        id: 2,
        text: 'Feed the Fish',
        day: 'April 12 at 3:00pm',
        reminder: true
      },
      {
        id: 3,
        text: 'Watch tv',
        day: 'April 12 at 6:00pm',
        reminder: false
      },
    ]
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
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

<template>
  <div id="app">
    <h1>To Do List</h1>

    <div id="input-wrapper">
      <input v-model="newTask" placeholder="Add Task" />
      <button @click="addTask">Add</button>
    </div>

    <div id="tasks-wrapper">
      <ol>
        <li
          v-for="(task, index) in tasks"
          :key="index"
          :class="{ done: task.done }"
        >
          {{ task.text }} <input type="checkbox" v-model="task.done" />
        </li>
      </ol>
    </div>

    <div id="delete-tasks">
      <h4>Delete completed tasks:</h4>
      <button @click="removeCompletedTasks(index)">Delete</button>
    </div>

    <div></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push({ text: this.newTask, done: false });
        this.newTask = '';
      }
    },
    removeCompletedTasks(index) {
      this.tasks = this.tasks.filter(task => !task.done);
    },
  },
};
</script>

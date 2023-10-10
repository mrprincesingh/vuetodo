<template>
  <div id="app" class="container mt-5">
    <TaskCreation @create="addTask" />
    <TaskFilter @filter="setFilter" />
    <TaskList
      :tasks="filteredTasks"
      @toggle="toggleTask"
      @delete="deleteTask"
      @edit="editTask"
    />
  </div>
</template>

<script>
import TaskCreation from './components/TaskCreation.vue';
import TaskFilter from './components/TaskFilter.vue';
import TaskList from './components/TaskList.vue';

export default {
  components: {
    TaskCreation,
    TaskFilter,
    TaskList,
  },
  data() {
    return {
      tasks: [],
      filter: 'all',
    };
  },
  computed: {
    filteredTasks() {
      if (this.filter === 'completed') {
        return this.tasks.filter((task) => task.completed);
      } else if (this.filter === 'incomplete') {
        return this.tasks.filter((task) => !task.completed);
      }
      return this.tasks;
    },
  },
  methods: {
    addTask(title) {
      this.tasks.push({ title, completed: false });
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    setFilter(filterType) {
      this.filter = filterType;
    },
    toggleTask(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    },
    editTask(index) {
      const newTitle = prompt('Edit task', this.tasks[index].title);
      if (newTitle !== null) {
        this.tasks[index].title = newTitle;
      }
    },
  },
};
</script>

<style>
.completed {
  text-decoration: line-through;
}
</style>

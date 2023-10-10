<template>
  <div>
    <h2 class="task-list-heading">Task List</h2>
    <ul class="list-group">
      <li
        class="list-group-item task-item"
        v-for="(task, index) in tasks"
        :key="index"
      >
        <span :class="{ 'completed': task.completed }">{{ task.title }}</span>
        <div class="task-buttons">
          <button class="btn btn-primary btn-sm" @click="editTask(index)">Edit</button>
          <button class="btn btn-danger btn-sm" @click="deleteTask(index)">Delete</button>
          <button class="btn btn-info btn-sm" @click="toggleTask(index)">
            {{ task.completed ? 'Mark Incomplete' : 'Mark Complete' }}
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    tasks: Array,
  },
  methods: {
    toggleTask(index) {
      // Emit the 'toggle' event with the task index
      this.$emit('toggle', index);
    },
    editTask(index) {
      this.$emit('edit', index);
    },
    deleteTask(index) {
      this.$emit('delete', index);
    },
  },
};
</script>

<style scoped>
.task-list-heading {
  font-size: 24px;
  margin-bottom: 20px;
}

.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #fff;
}

.completed {
  text-decoration: line-through;
}

.task-buttons button {
  margin-left: 10px;
}

.task-buttons button:first-child {
  margin-left: 0;
}

/* Adjust button colors and sizes as needed */
.task-buttons button.btn-primary {
  background-color: #007bff;
}

.task-buttons button.btn-danger {
  background-color: #dc3545;
}

.task-buttons button.btn-info {
  background-color: #17a2b8;
}
</style>

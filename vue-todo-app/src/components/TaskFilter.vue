<template>
  <div>
    <h2 class="task-filtering-heading">Task Filtering</h2>
    <div class="btn-group">
      <button class="btn filter-button all-button" @click="filterTasks('all')">All</button>
      <button class="btn filter-button completed-button" @click="filterTasks('completed')">Completed</button>
      <button class="btn filter-button incomplete-button" @click="filterTasks('incomplete')">Incomplete</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    filterTasks(filterType) {
      this.$emit('filter', filterType);
    },
  },
};
</script>

<style scoped>
.task-filtering-heading {
  font-size: 24px;
  margin-bottom: 20px;
}

.filter-button {
  border-radius: 5px;
  margin-right: 10px;
  padding: 10px 20px;
  color: #fff;
  font-weight: bold;
}

.all-button {
  background-color: #007bff; /* Blue */
}

.completed-button {
  background-color: #28a745; /* Green */
}

.incomplete-button {
  background-color: #ffc107; /* Yellow */
}

.filter-button:hover {
  opacity: 0.9;
}

.filter-button:focus {
  outline: none;
  box-shadow: none;
}
</style>

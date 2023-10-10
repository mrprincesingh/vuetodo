<template>
  <div>
    <h2 class="task-creation-heading">Task Creation</h2>
    <div class="input-group mb-3">
      <input
        type="text"
        class="form-control"
        placeholder="Enter task title"
        v-model="newTaskTitle"
        @keyup.enter="createTask"
      />
      <div class="input-group-append">
        <button class="btn btn-primary create-button" @click="createTask">Create</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTaskTitle: '',
    };
  },
  methods: {
    createTask() {
      if (this.newTaskTitle.trim() === '') return;
      this.$emit('create', this.newTaskTitle);
      this.newTaskTitle = '';
    },
  },
};
</script>

<style scoped>
.task-creation-heading {
  font-size: 24px;
  margin-bottom: 20px;
}

.input-group {
  width: 100%;
}

.form-control {
  border-radius: 5px;
}

.create-button {
  border-top-left-radius: 0;
  border-bottom-left-radius: 0;
}
</style>

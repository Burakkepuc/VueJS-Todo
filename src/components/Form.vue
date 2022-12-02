<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input
        v-model="taskName"
        type="text"
        name="text"
        placeholder="Task Header"
      />
    </div>
    <div class="form-control">
      <label>Description</label>
      <input
        v-model="description"
        type="text"
        name="text"
        placeholder="Task Description"
      />
    </div>
    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: 'Form',
  data() {
    return {
      taskName: '',
      description: '',
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();

      if (!this.taskName) {
        alert('Please add a task');
        return;
      }

      const newFormTask = {
        id: Math.random() * 10000000,
        task: this.taskName,
        description: this.description,
      };

      this.$emit('add-task', newFormTask);

      this.taskName = '';
      this.description = '';
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
</style>

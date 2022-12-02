<template>
  <div class="task">
    <ul>
      <li v-for="task in tasks">
        <h4>
          {{ task.task }}
          <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
        </h4>
        <div class="left">
          <p>{{ task.description }}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Tasks',
  props: {
    tasks: Array,
  },
};
</script>

<style scoped>
div {
  text-align: center;
}
li {
  list-style-type: none;
  font-size: 15px;
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
}
.fas {
  cursor: pointer;
  color: red;
  font-weight: bold;
}
h4 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.left {
  display: flex;
  gap: 20px;
  margin: 10px;
}
input[type='checkbox']:checked {
  border: solid 1px;
}
</style>

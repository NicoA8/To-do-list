<template>
  <div :class="[task.important ? 'important' : '', 'task']">
    <div class="text">
      <h3>
        {{ task.text }}
      </h3>
      <p>{{ task.day }}</p>
    </div>
    <div class="buttons">
      <button @click="$emit('delete-task', task.id)" class="x-btn">X</button>
      <button @click="$emit('mark-task', task.id)" class="imp-btn">!!</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "EachTask",
  props: {
    task: Object,
  },
};
</script>

<style scope>
.task {
  background: #fff;
  border: 0.1rem solid #adadad;
  margin: 1rem;
  padding: 10px 20px;
  display: flex;
  justify-content: space-between;
  border-left: 5px solid lightseagreen;
}
.task.important {
  box-shadow: -0.5rem 0rem goldenrod;
}
.buttons {
  display: flex;
  gap: 2rem;
}
.buttons button {
  font-weight: bold;
  font-size: 1.3rem;
  border: none;
  cursor: pointer;
  background-color: transparent;
}
.x-btn {
  color: lightcoral;
}
.imp-btn {
  color: goldenrod;
  font-weight: bold;
  border: none;
  cursor: pointer;
  background-color: transparent;
}
</style>

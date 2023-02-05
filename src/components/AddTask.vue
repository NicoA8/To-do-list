<template>
  <form @submit="handleSubmit">
    <label>
      Task
      <input v-model="text" type="text" name="text" placeholder="Add Task" />
      <div v-if="filled" class="fill">please fill all.</div>
    </label>
    <label>
      Day & Time
      <input
        v-model="day"
        type="text"
        name="day"
        placeholder="Add Day & Time"
      />
      <div v-if="filled" class="fill">please fill all.</div>
    </label>
    <label>
      Is it important?
      <input v-model="important" type="checkbox" name="important" />
      <div v-if="filled" class="fill">please fill all.</div>
    </label>
    <input type="submit" value="Save Task" class="save-btn" />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: "",
      day: "",
      important: false,
      filled: false,
    };
  },
  methods: {
    handleSubmit(event) {
      event.preventDefault();
      if (!this.text || !this.day || !this.important) {
        this.filled = true;
        return;
      }
      const newTask = {
        id: this.text,
        text: this.text,
        day: this.day,
        important: this.important,
      };
      this.text = "";
      this.day = "";
      this.important = false;
      this.filled = false;

      this.$emit("add-task", newTask);
    },
  },
};
</script>

<style scoped>
form,
label {
  display: grid;
  justify-items: center;
  gap: 0.5rem;
}
label {
  margin: 0.5rem;
  font-weight: bold;
  text-transform: uppercase;
}
input {
  width: 12rem;
  padding: 0.5rem;
}
.save-btn {
  background-color: lightseagreen;
  color: #fff;
  border: none;
  padding: 0.5rem;
  margin: 5px;
  width: 8rem;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 1rem;
  font-family: inherit;
  transition: all 0.5s;
}
.save-btn:active,
.save-btn:hover,
.save-btn:focus {
  transform: scale(1.05);
}
.fill {
  color: lightcoral;
  font-size: 0.5rem;
}
</style>

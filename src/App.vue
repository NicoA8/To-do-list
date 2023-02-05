<template>
  <div class="container">
    <MyHeader
      @show-form="toggleForm"
      title="Task Manager"
      :showForm="showForm"
    />
    <div v-show="showForm">
      <AddTask @add-task="addTask" />
    </div>
    <TasksList @delete-task="deleteTask" @mark-task="markTask" :tasks="tasks" />
  </div>
</template>

<script>
import MyHeader from "./components/MyHeader.vue";
import TasksList from "./components/TasksList.vue";
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: {
    MyHeader,
    TasksList,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showForm: false,
    };
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    toggleForm() {
      this.showForm = !this.showForm;
    },
    deleteTask(id) {
      console.log("delete task", id);
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    markTask(id) {
      console.log("mark task", id);
      this.tasks = this.tasks.map((task) =>
        task.id === id
          ? {
              ...task,
              important: !task.important,
            }
          : task
      );
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctor",
        day: "May 4th at 7:30pm",
        important: true,
      },
      {
        id: 2,
        text: "Pick up package",
        day: "May 4th at 12:00pm",
        important: true,
      },
      {
        id: 3,
        text: "Grab coffee",
        day: "May 4th at 2:30pm",
        important: false,
      },
      {
        id: 4,
        text: "Meeting",
        day: "May 4th at 4:00pm",
        important: true,
      },
      {
        id: 5,
        text: "Movie",
        day: "May 4th at 7:30pm",
        important: false,
      },
      {
        id: 6,
        text: "Fold laundry",
        day: "May 4th at 10:00pm",
        important: false,
      },
    ];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 2px solid lightslategray;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
  transition: all 0.5s;
}
.btn:active,
.btn:hover,
.btn:focus {
  transform: scale(1.1);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>

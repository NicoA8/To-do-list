<template>
  <div :key="task.id" v-for="task in tasks">
    <EachTask
      @delete-task="$emit('delete-task', task.id)"
      @mark-task="$emit('mark-task', task.id)"
      :task="task"
    />
  </div>
</template>

<script>
import EachTask from "./EachTask.vue";

export default {
  name: "TasksList",
  props: {
    tasks: Array,
  },
  components: {
    EachTask,
  },
  emits: ["delete-task", "mark-task"],
};
</script>

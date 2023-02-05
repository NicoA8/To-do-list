<template>
  <header>
    <h1>{{ title }}</h1>
    <AddButton
      @show="$emit('show-form')"
      :text="showForm ? 'Close' : 'Add Task'"
      :color="showForm ? 'darkred' : 'lightseagreen'"
    />
  </header>
</template>

<script>
import AddButton from "./AddButton.vue";
export default {
  name: "MyHeader",
  props: {
    title: String,
    showForm: Boolean,
  },
  components: {
    AddButton,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 2rem;
}
</style>

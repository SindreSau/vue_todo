<template>
  <li>{{ props.todo }}</li>
</template>

<script setup>
// Props
const props = defineProps({
  todo: {
    type: Object,
    required: true
  }
})
</script>

<style scoped>
li {
  list-style: none;
  padding: 10px;
  background-color: #363a47;
  border-radius: 10px;
  box-shadow: -3px 3px 10px rgba(0, 0, 0, 0.15);

  cursor: pointer;
  transition: background-color 0.15s;
}

li:hover {
  background-color: #626a83;
}
</style>

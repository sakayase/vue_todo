<template>
  <li v-if="completed" class="completed">
    {{ title }}
    <img
      class="completed-svg"
      src="../assets/check-circle-regular.svg"
      v-on:click="completed = !completed"
    />
    <img
      src="../assets/times-circle-solid.svg"
      class="delete-svg"
      @click="removeTask(id)"
    />
  </li>
  <li v-else class="notCompleted">
    {{ title }}
    <img
      class="notCompleted-svg"
      src="../assets/circle-regular.svg"
      v-on:click="completed = !completed"
    />
    <img
      src="../assets/times-circle-solid.svg"
      class="delete-svg"
      @click="removeTask(id)"
    />
  </li>
</template>

<script>
export default {
  name: "Task",
  props: {
    title: String,
    completed: Boolean,
    id: Number,
  },
  methods: {
    removeTask: function (id) {
        console.log(id)
    },
  },
};
</script>
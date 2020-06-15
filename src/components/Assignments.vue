<template>
  <div>
    <div v-bind:key="assignment.id" v-for="assignment in assignments">
      <AssignmentItem
        v-bind:assignment="assignment "
        v-on:delete-assignment="$emit('delete-assignment', assignment.id)"
      />
    </div>
  </div>
</template>

<script>
import AssignmentItem from "./AssignmentItem";

export default {
  name: "Assignments",
  components: {
    AssignmentItem
  },
  props: ["assignments"]
};
</script>


<style scoped>
</style>
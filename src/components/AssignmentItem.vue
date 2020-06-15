<template>
  <div class="assignment-item" v-bind:class="{'is-complete': assignment.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" />
      {{assignment.title}}
      <button
        @click="$emit('delete-assignment', assignment.id)"
        class="delete"
      >X</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "AssignmentItem",
  props: ["assignment"],
  methods: {
    markComplete() {
      this.assignment.completed = !this.assignment.completed;
    }
  }
};
</script>

<style scoped>
.assignment-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.is-complete {
  text-decoration: line-through;
}

.delete {
  background: red;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50px;
  cursor: pointer;
  float: right;
}
</style>
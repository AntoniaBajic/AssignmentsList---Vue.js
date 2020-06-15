<template>
  <div id="app">
    <Header />
    <AddAssignment v-on:add-assignment="addAssignment" />
    <Assignments
      v-bind:assignments="assignments"
      v-on:delete-assignment="deleteAssignment"
    />
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Assignments from './components/Assignments';
import AddAssignment from './components/AddAssignments';

export default {
  name: 'App',
  components: {
    Assignments,
    Header,
    AddAssignment,
  },
  data() {
    return {
      assignments: [
        {
          id: 1,
          title: 'First assignment',
          completed: true,
        },
        {
          id: 2,
          title: 'Second assignment',
          completed: false,
        },
        {
          id: 3,
          title: 'Third assignment',
          completed: false,
        },
      ],
    };
  },
  methods: {
    deleteAssignment(id) {
      this.assignments = this.assignments.filter(
        (assignment) => assignment.id !== id
      );
    },
    addAssignment(newAssignment) {
      this.assignments = [...this.assignments, newAssignment];
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: rgb(46, 138, 81);
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
</style>

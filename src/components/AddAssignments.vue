<template>
  <div>
    <form @submit="addAssignment">
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="Add Assignment"
      />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'AddAssignment',
  data() {
    return {
      title: '',
    };
  },
  methods: {
    addAssignment(e) {
      e.preventDefault();
      const newAssignment = {
        id: uuidv4(),
        title: this.title,
        completed: false,
      };
      // Send to parent
      this.$emit('add-assignment', newAssignment);

      this.title = '';
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}

input[type='text'] {
  flex: 10;
  padding: 5px;
}

input[type='submit'] {
  flex: 2;
}
</style>

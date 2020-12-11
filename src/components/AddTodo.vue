<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Todo...">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
  name: "AddTodo",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo(e) {
      e.preventDefault();

      const newTodo = {
        id: uuidv4(),
        title: this.title,
        completed: false
      }
      // Send up to parent
      this.$emit('add-todo', newTodo);

      this.title = '';
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
    padding: 0 20px;
  }

  input[type="text"] {
    flex: 10;
    padding: 15px 20px;
    border: none;
    border-radius: 2px 0 0 2px;
  }

  input[type="submit"] {
    flex: 2;
    border: none;
    border-radius: 0 2px 2px 0;
    cursor: pointer;
  }
</style>


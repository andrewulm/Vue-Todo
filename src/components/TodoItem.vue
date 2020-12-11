<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete">
      {{ todo.title }}
      <button @click="$emit('del-todo', todo.id)" class="del">X</button>
    </p>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo'],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
}
</script>

<style scoped>
  .todo-item {
    background: #e8e8e8;
    color: #333333;
    padding: 10px 20px;
    border-left: 5px solid #89beb3;
    border-radius: 2px;
    margin-bottom: 20px;
  }

  .is-complete {
    text-decoration: line-through;
  }

  .del {
    background: #c75643;
    color: white;
    padding: 5px 8px;
    border-radius: 5px;
    border: none;
    cursor: pointer;
    float: right;
  }
</style>
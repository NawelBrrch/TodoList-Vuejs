<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete">
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
      </p>
  </div>
  
</template>

<script>
export default {
  name: 'TodoItem',
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
}
</script>

<style scoped>

  .todo-item {
      background: #087E8B;
      padding: 10px;
      border-bottom: 1px #ccc dotted;
      margin: 2vw 0;
      color: #F5F5F5;
      font-weight: bold;
      font-size: 2vw;
    }
  .is-complete {
    text-decoration: line-through;
    background-color: #3C3C3C;
  }
  .del {
    background: #FF5A5F;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }

</style>
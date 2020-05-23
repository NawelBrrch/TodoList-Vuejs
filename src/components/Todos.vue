<template>
  <div class="todoContainer">
    <div v-bind:key="todo.id" v-for="todo in todos">
      <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem';

export default {
  name: 'Todos',
  components: {
    TodoItem
  },
  props: ['todos']
  
}
</script>

<style scoped>

  .todoContainer {
    width: 50vw;
    margin-left:auto;
    margin-right:auto;
  }



</style>
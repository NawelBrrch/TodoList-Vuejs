<template>
  <div class="formContainer">
    <form @submit.prevent="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Todo...">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>

import {uuid} from 'vue-uuid';


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
        id: uuid.v4(),
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
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
    color: #087E8B;
    font-weight: bold;
    font-size: 2vw;
    border: 2px solid #087E8B;

  }
  input[type="submit"] {
    flex: 2;
    background-color: #FF5A5F;
    color: #3C3C3C;
    font-weight: bold;
    font-size: 2vw;
    border: 2px solid #FF5A5F;
  }

  .formContainer {
    margin: 3vw 0;
    width: 50vw;
    margin-left:auto;
    margin-right:auto;
  }
</style>
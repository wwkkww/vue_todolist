<template>
  <div>
    <form @submit.prevent="addTodo">
    <!-- <form v-on:submit.prevent="addTodo"> -->
      <input type="text" v-model="newTitle" name="title" placeholder="Add todo...">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>
// import uuid from 'uuid';

export default {
  name: "AddTodo",
  data() {
    return {
      newTitle: ''
    }
  },
  methods: {
    addTodo() {
      const newTodo = {
        // id: uuid.v4(),
        title: this.newTitle,
        completed: false
      }
      //Send to parent
      this.$emit('add-todo', newTodo);
      this.newTitle = "";
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
  }

  input[type="submit"]{
    flex: 2;
  }
</style>



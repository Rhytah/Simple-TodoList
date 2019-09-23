<template>
  <div>
    <form @submit.prevent="addTodo">
      <input type="text" name="title" v-model="title" placeholder="Add todo ....." />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>
<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        title: this.title,
        completed: false
      };
      //send up to parent
      this.$emit("add-todo", newTodo);
      this.title = "";
    }
  }
};
</script>
<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
  font-size: 16px;
}
input[type="submit"] {
  flex: 2;
  background-color: rgb(18, 94, 94);
  color: antiquewhite;
  border-radius: 1em;
  font-size: 14px;
}
</style>
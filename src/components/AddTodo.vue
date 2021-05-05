<template>
  <form class="todo-form">
    <input type="text" value="akhsb" />
    <input type="submit" value="Add" />
  </form>
</template>

<script>
export default {
  name: "add-todo",
};
</script>

<style scoped>
.todo-form {
  width: 100%;
  display: flex;
  align-items: center;
  margin-bottom: 40px;
}
input {
  height: 40px;
  border-radius: 15px;
  border: none;
  border-bottom: 4px solid #0f81ce;
  font-size: 20px;
  outline: none;
}
input[type="text"] {
  width: 100%;
  padding-left: 10px;
}
input[type="text"]:focus {
  background-color: #f4faff;
}
input[type="submit"] {
  margin-left: 5px;
  padding: 0 10px;
  background-color: white;
}
</style>

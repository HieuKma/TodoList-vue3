<template>
  <form class="todo-form" @submit="addItem">
    <input type="text" placeholder="Add todo" v-model="title" />
    <input type="submit" value="Add" />
  </form>
</template>

<script>
import { ref } from 'vue';
import {v4 as uuidv4} from 'uuid';
export default {
  name: "add-todo",
  setup(props, context) {
    const title = ref('');

    const addItem = (e) => {
        e.preventDefault();
        context.emit('add-todo', {
            id: uuidv4(), title: title.value, completed: false
        });
        title.value = '';
    }

    return { title, addItem }
  }
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

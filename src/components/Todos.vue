<template>
  <div class="todo__content">
    <add-todo></add-todo>
    <div class="todo__list">
      <TodoItem 
        v-for="(todo, index) in todos" 
        :key="index"
        :todoProps="todo"
        @item-completed="markCompeled"
        @delete-item="deleteItem"
      />
    </div>
  
  </div>
</template>

<script>
import { ref } from 'vue'

import TodoItem from './TodoItem';
import AddTodo from './AddTodo';

export default {
  name: 'Todos',
  components: { TodoItem, AddTodo },
  setup() {
    const todos = ref([
      { id: 1, title: 'Viec 1', isComplete: false },
      { id: 2, title: 'Viec 2', isComplete: true },
      { id: 3, title: 'Viec 3', isComplete: false },
    ])

    const markCompeled = id => {
      todos.value.map(item => {
        if(item.id === id) item.isComplete = !item.isComplete;
      })
    }

    const deleteItem = id => {
      todos.value = todos.value.filter(item => item.id !== id )
    }

    return {
      todos,
      markCompeled,
      deleteItem
    }
  }
}
</script>

<style>
.todo__content {
  margin: 0 15px;
}
</style>

<template>
  <div class="todo__content">
    <add-todo @add-todo="handleAddItem"></add-todo>
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
import { ref } from 'vue';
import {v4 as uuidv4} from 'uuid';

import TodoItem from './TodoItem';
import AddTodo from './AddTodo';

export default {
  name: 'Todos',
  components: { TodoItem, AddTodo },
  setup() {
    const todos = ref([
      { id: uuidv4(), title: 'Viec 1', isComplete: false },
      { id: uuidv4(), title: 'Viec 2', isComplete: true },
      { id: uuidv4(), title: 'Viec 3', isComplete: false },
    ])

    const markCompeled = id => {
      todos.value.map(item => {
        if(item.id === id) item.isComplete = !item.isComplete;
      })
    }

    const deleteItem = id => {
      todos.value = todos.value.filter(item => item.id !== id )
    }

    const handleAddItem = todo => {
      todos.value.push(todo);
    }

    return {
      todos,
      markCompeled,
      deleteItem,
      handleAddItem
    }
  }
}
</script>

<style>
.todo__content {
  margin: 0 15px;
}
</style>

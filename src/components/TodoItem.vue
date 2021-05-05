<template>
  <div class="todo__item" :class="todoProps.isComplete ? 'todo__item--is-completed' : ''">
    <div class="todo__item-data">
      <input type="checkbox"
        :checked="todoProps.isComplete"
        @change="markItemCompeled">
      <p>{{ todoProps.title }}</p>
    </div>
    <button class="todo__item-delete" @click="deleteItem">
      <i class="far fa-trash-alt"></i>
    </button>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todoProps'],
  setup(props, context) {
    const markItemCompeled = () => {
      context.emit('item-completed', props.todoProps.id);
    }

    const deleteItem = () => {
      context.emit('delete-item', props.todoProps.id);
    }

    return {
      markItemCompeled,
      deleteItem
    }
  }
}
</script>

<style scoped>
.todo__item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 0;
  border-bottom: 1px solid rgb(182, 182, 182);
}
.todo__item--is-completed {
  text-decoration: line-through;
  color: rgb(82, 82, 82);
}
.todo__item-data {
  display: flex;
  align-items: center;
}
input {
  width: 20px;
  height: 20px;
  margin-right: 10px;
}
i {
  font-size: 15px;
}
.todo__item-delete {
  
}
</style>
<template>
  <form class="todo-actions">
    <button @click.prevent="$emit('todosRemoved')" id="delete-todos">
      Remove done Todos
    </button>
  </form>
</template>

<style scoped>
.todo-actions {
  padding-left: 2rem;
}

.todo-actions > button {
  height: 2rem;
  aspect-ratio: 6;
  font-size: 1rem;
  margin: 0.75rem 0 3rem;
}
</style>

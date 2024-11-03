<script setup></script>

<template>
  <TodoHeader />
  <TodoInput v-on:addTodoClicked="addTodo" />
  <TodoFilter v-on:filterChanged="filterTodos" />
  <TodoActions v-on:todosRemoved="removeTodos" />
  <TodoOutput :filterTodos="this.filteredTodos" />
</template>

<script>
import TodoHeader from '@/components/TodoHeader.vue'
import TodoInput from '@/components/TodoInput.vue'
import TodoFilter from '@/components/TodoFilter.vue'
import TodoActions from '@/components/TodoActions.vue'
import TodoOutput from '@/components/TodoOutput.vue'
export default {
  components: {
    TodoHeader,
    TodoInput,
    TodoFilter,
    TodoActions,
    TodoOutput,
  },
  data() {
    return {
      allTodos: [],
      filteredTodos: [],
      filter: 'filter-all',
    }
  },
  created() {
    this.allTodos = [
      {
        id: 'id-' + window.crypto.randomUUID(),
        done: true,
        protected: true,
        description: 'Learn Vue',
      },
      {
        id: 'id-' + window.crypto.randomUUID(),
        done: false,
        protected: true,
        description: 'Learn Python',
      },
    ]
    this.filteredTodos = this.allTodos
  },

  computed: {},

  methods: {
    addTodo(description) {
      let id = 'id-' + window.crypto.randomUUID()
      this.allTodos.push({
        id: id,
        done: false,
        protected: true,
        description: description,
      })
      description = ''
      console.log(this.allTodos)
    },
    filterTodos(target) {
      this.filter = target.id
      if (this.filter === 'filter-all') {
        this.filteredTodos = this.allTodos
      } else if (this.filter === 'filter-done') {
        this.filteredTodos = this.allTodos.filter(todo => todo.done === true)
      } else if (this.filter === 'filter-open') {
        this.filteredTodos = this.allTodos.filter(todo => todo.done === false)
      }
    },
    removeTodos() {
      this.allTodos = this.allTodos.filter(todo => todo.done === false)
      this.filteredTodos = this.allTodos
    },
  },
}
</script>

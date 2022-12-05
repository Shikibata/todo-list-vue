<template>
  <form @submit.prevent="addItemAndClear(todo)">
    <input v-model="todo" type="text" class="bg-blue"/><button>Add</button>
  </form>
</template>

<script>
import { useTodoListStore } from '../store/useTodoListStore'
import {ref, watch} from "vue";
export default {
  setup() {
    const todo = ref('')
    // use Pinia store:
    const store = useTodoListStore();

    function addItemAndClear(item) {
      if (item.length === 0) {
        return
      };
      // invokes function in the store:
      store.addTodo(item)
      todo.value = ''
    }
    return { todo, addItemAndClear, store }
  },

}
</script>
<style scoped>

</style>
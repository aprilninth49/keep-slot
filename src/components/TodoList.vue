
<template>
  <div>
    <token-counter :number="tokenNumber"></token-counter>
    <button @click="showCreate=true">
      New Todo</button>
    <todo-create v-show="showCreate"
                 @createTodo="createTodo"
                 @cancelTodo="cancelTodo"></todo-create>
    <todo-edit v-show="editState"
               @hideEdit="hideEdit"></todo-edit>
    <todo-item v-for="(item, index) in items"
               :key="item.k"
               :todo-detail="item.todo"
               :fre-detail="item.frequency"
               @doneTodo="doneTodo"
               @showEdit="showEdit"
               @remove="remove"></todo-item>
  </div>
</template>

<script>
import TokenCounter from './tokenCounter.vue'
import TodoItem from './TodoItem.vue'
import TodoCreate from './TodoCreate.vue'
import TodoEdit from './TodoEdit.vue'
export default {
  name: 'item',
  components: {
    'token-counter': TokenCounter,
    'todo-item': TodoItem,
    'todo-create': TodoCreate,
    'todo-edit': TodoEdit
  },
  data() {
    return {
      tokenNumber: 0,
      showCreate: false,
      editState: false,
      k: 2,
      items: [
        {
          k: 0,
          todo: 'read news',
          frequency: 'everyday'
        },
        {
          k: 1,
          todo: 'clean litter box',
          frequency: 'everyweek'
        }
      ]
    }
  },
  computed: {
    a() {
      return this.items.length
    }
  },
  methods: {
    createTodo(item) {
      this.items.unshift(Object.assign({}, item, { k: this.k++ }));
      this.showCreate = false;
    },
    cancelTodo() {
      this.showCreate = false;
    },
    doneTodo() {
      this.tokenNumber = this.tokenNumber += 1;
    },
    showEdit() {
      this.editState = true;
    },
    hideEdit() {
      this.editState = false;
    },
    remove(index) {
      return this.items.splice(index, 1);
    }
  }
}
</script>


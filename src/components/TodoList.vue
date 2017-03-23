
<template>
  <div>
    <token-counter></token-counter>
    <button @click="showCreate=true">
      New Todo</button>
    <todo-create v-show="showCreate"
                 @createTodo="createTodo"
                 @cancelTodo="cancelTodo"></todo-create>
    <todo-item v-for="item in items"
               :todo-detail="item.todo"
               :fre-detail="item.frequency"
               :number="tokenNumber"
               @doCount="doCount"
               @showEdit="showEdit"
               @remove="remove"></todo-item>
  </div>
</template>

<script>
import TokenCounter from './tokenCounter.vue'
import TodoItem from './TodoItem.vue'
import TodoCreate from './TodoCreate.vue'
export default {
  name: 'item',
  components: {
    'token-counter': TokenCounter,
    'todo-item': TodoItem,
    'todo-create': TodoCreate
  },
  data() {
    return {
      tokenNumber:0,
      showCreate: false,
      items: [
        {
          todo: 'read news',
          frequency: 'everyday'
        },
        {
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
      this.items.unshift(item);
      this.showCreate = false;
    },
    cancelTodo() {
      this.showCreate = false;
    },
    doCount(){
      this.tokenNumber=this.tokenNumber+=1;
    },
    showEdit() {
      this.showCreate = true;
    },
    remove(index) {
      return this.items.splice(index, 1);
    }
  }
}
</script>


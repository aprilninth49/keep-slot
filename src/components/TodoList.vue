<template>
  <div>
    <fieldset>
      <legend>Create New Todo</legend>
      <label>Todo:</label>
      <input type="text"
             v-model='newList.todo'></input>
      <label>Frequency:</label>
      <select v-model='newList.frequency'>
        <option value='everyday'>everyday</option>
        <option value='everyweek'>everyweek</option>
        <option value='onlyonce'>onlyonce</option>
      </select>
      <button @click='createTodo'>add</button>
    </fieldset>
    <todo-item v-for='list in lists'
               :todo-detail='list.todo'
               :fre-detail='list.frequency'></todo-item>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue'
export default {
  name: 'List',
  components: {
    'todo-item': TodoItem
  },
  data() {
    return {
      newList: {
        todo: '',
        frequency: 'onlyonce'
      },
      lists: [
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
      return this.lists.length
    }
  },
  methods: {
    createTodo: function () {
      this.lists.push(this.newList);
      this.newList = { todo: '', frequency: 'onlyonce' }
    }
  }
}
</script>


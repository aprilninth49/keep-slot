<template>
  <fieldset>
    <legend>Create New Todo</legend>
    <label>Todo:</label>
    <input type="text"
           v-model='newItem.todo'></input>
    <label>Frequency:</label>
    <select v-model='newItem.frequency'>
      <option value='everyday'>everyday</option>
      <option value='everyweek'>everyweek</option>
      <option value='onlyonce'>onlyonce</option>
    </select>
    <button @click='createTodo'>ok</button>
    <button @click='$emit("cancelTodo")'>cancel</button>
  </fieldset>
</template>

<script>
export default {
  name: 'create',
  data() {
    return {
      newItem: {
        todo: '',
        frequency: 'onlyonce'
      }
    }
  },
  methods: {
    createTodo() {
      this.$emit("createTodo", this.newItem);
      this.newItem = { todo: '', frequency: 'onlyonce' };
    },

  }
}
</script>

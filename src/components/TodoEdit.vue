<template>
  <div>
    <label>Todo:</label>
    <input type="text"
           v-model="todo"></input>
    <label>Frequency:</label>
    <select v-model="frequency">
      <option value='everyday'>everyday</option>
      <option value='everyweek'>everyweek</option>
      <option value='onlyonce'>onlyonce</option>
    </select>
    <button @click="$emit('doneEdit',todo,frequency)">ok</button>
    <button @click="$emit('hideEdit')">cancel</button>
  </div>
</template>

<script>
export default {
  name: 'todoEdit',
  props: ['itemIndex', 'editTodo', 'editFrequency'],
  data() {
    return {
      todo: this.editTodo,
      frequency: this.editFrequency
    }
  },
  watch: {
    editTodo(val) {
      this.todo = val;
    },
    editFrequency(val) {
      this.frequency = val;
    }
  }

}

</script>

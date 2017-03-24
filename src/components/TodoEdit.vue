<template>
  <div>
    <label>Todo:</label>
    <input type="text"></input>
    <label>Frequency:</label>
    <select>
      <option value='everyday'>everyday</option>
      <option value='everyweek'>everyweek</option>
      <option value='onlyonce'>onlyonce</option>
    </select>
    <button>ok</button>
    <button @click="$emit('hideEdit')">cancel</button>
  </div>
</template>

<script>
export default {
  name: 'todoEdit',

}

</script>

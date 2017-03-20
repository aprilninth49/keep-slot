<template>
  <div>
    <span>Todo:</span>
    <span>{{todoDetail}}</span>
    <span>Frequency:</span>
    <span>{{freDetail}}</span>
    <button>delete</button>
  </div>
</template>

<script>
export default {
  name: 'Todo-Item',
  props: ['todoDetail', 'freDetail']
}
</script>


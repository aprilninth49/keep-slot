<template>
  <div>
    <span>Todo:</span>
    <span>{{todoDetail}}</span>
    <span>Frequency:</span>
    <span>{{freDetail}}</span>
    <button @click='$emit("doCount")'>done!</button>
    <button @click='$emit("showEdit")'>edit</button>
    <button @click='$emit("remove")'>delete</button>
  </div>
</template>

<script>
export default {
  name: 'Todo-Item',
  props: ['todoDetail', 'freDetail']
}

</script>


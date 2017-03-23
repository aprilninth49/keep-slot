<template>
  <div>
    <label>{{textName}}</label>
    <label>{{choiceName}}</label>
  </div>
</template>

<script>
export default {
  name: 'child',
  props: ['textName', 'choiceName']
}
</script>

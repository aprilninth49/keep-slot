<template>
  <div>
    <header>
      Todo List
    </header>
    <test-child :text-name="labelName.textName"
                :choice-name="labelName.choiceName"></test-child>
  </div>
</template>

<script>
import TestChild from './TestChild.vue'
export default {
  name: 'test-header',
  components: {
    'test-child': TestChild
  },
  data() {
    return {
      labelName: {
        textName: 'todo:',
        choiceName: 'frequency:'
      }
    }
  }
}
</script>

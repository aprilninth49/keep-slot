<template>
  <q-layout>
    <div slot="header" class="toolbar">
      <button class>
        <i>keyboard_arrow_left</i>
      </button>
      <q-toolbar-title class="headerStander">
        {{toolbarTitle}}
      </q-toolbar-title>
    </div>
    <div class="layout-view">
      <button class="addButton primary outline">
        <i>add_circle_outline</i>
        <span>新建</span>
      </button>
    </div>
  </q-layout>


</template>

<script>
  export default {
    data() {
      return {
        toolbarTitle: "Todo List"
      }
    }
  }

</script>


<style scoped>
  .headerStander{
    padding-right: 1.5rem;
    text-align: center;
  .addButton{
    width:100%;
  }
    /*background-color: #A5DEE4;*/
  }
</style>

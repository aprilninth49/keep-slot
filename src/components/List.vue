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
        <i>add</i>
      </button>
      <div class="list">
          <div class="item two-lines">

            <img class="item-primary" :src="'statics/boy-avatar.png'">
            <div class="item-content has-secondary">
              <div>读两篇英文新闻。</div>
              <div>每天</div>
            </div>
            <div class="item-secondary stamp">
              未完成
            </div>
            <q-range v-model="percentage" class="slider" :min="0" :max="1" :step="1"></q-range>
          </div>
        </div>
    </div>

  </q-layout>


</template>

<script>
  import { Dialog } from 'quasar'
  export default {
    data() {
      return {
        toolbarTitle: "我的努力",
        percentage: 0

      }
    }
  }

</script>


<style>
  .headerStander{
    padding-right: 1.5rem;
    text-align: center;
  }
  .addButton{
    width:100%;
    margin:2rem 0;
    padding:1.5rem;
  }
  .addButton>i{
    font-size:2.8rem;
  }
   /*background-color: #A5DEE4;*/
  /*.slider {
    position: absolute;
  }*/
  .q-range-track {
    height: 0px;
    background-color: white;
  }
  .q-range-handle {
    width: 100px;
    height: 150px;
    top: -100%;
    border-radius: 0%;
  }
  .handle-at-minimum {
    background-color: #027be3 !important;
  }
  .q-range-handle.dragging {
    transform: matrix(0.690265, 0, 0, 0.690265, -46.9295, -70.3942);
  }

</style>

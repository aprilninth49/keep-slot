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
      <button v-on:click="openBox" class="addButton primary outline">
        <i>add</i>
      </button>
      <div class="list">
          <div class="item two-lines">
            <img class="item-primary" :src="'statics/boy-avatar.png'">
            <div class="item-content has-secondary">
              <div>{{commentTodo}}</div>
              <div>每天</div>
            </div>
            <div class="item-secondary stamp">
              未完成
            </div>
            <!--<q-range v-model="percentage" class="slider" :min="0" :max="1" :step="1"></q-range>-->
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
        // percentage: 0,
        commentTodo:'',
        optionData: {
          times:['everyday','everyweek','onlyOnce'],
          difficulty: 0
        }
      }
    },

    methods: {
      openBox: function(){
        Dialog.create({
        title: '编辑详情',
        form: {
          comments: {
            type: 'textarea',
            label: '我要做的努力是：',
            model: 'commentTodo'
          },
          //message:'你需要重复做这件事吗？请选择频率。',
          option: {
            type: 'radio',
            model:'optionData.times',
            items:[
              {label:'一次性',value:'optionData.times[2]'},
              {label:'每天',value:'optionData.times[0]'},
              {label:'每周',value:'optionData.times[1]'},
            ]
          },
          rating: {
            type: 'rating',
            class:'primary',
            label:'做成这件事有多难？请选择难度。',
            model:0,//这里固定写一个值，那用户输入的rating值存在哪里？
            max:5,
          },
          // 在form里面可以用下拉框吗？待确认。
          // select: {
          //   type: 'list',
          //   model:'',
          //   options:'optionData.times'
          // },
        },
        buttons: [
          '取消',
          {
            label: '完成',
             handler (data) {
              Toast.create('Returned ' + JSON.stringify(data))
             }
           }
         ]
      })
     }
    }
  }

</script>


<style>
  .headerStander {
    padding-right: 1.5rem;
    text-align: center;
  }
  .addButton {
    width: 100%;
    margin: 2rem 0;
    padding: 1.5rem;
  }
  .addButton>i {
    font-size: 2.8rem;
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
    width: 150px;
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

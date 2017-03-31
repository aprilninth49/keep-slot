<template>
  <div>
    <span>Todo:</span>
    <span>{{todoDetail}}</span>
    <span>Frequency:</span>
    <span>{{freDetail}}</span>
    <span>Diffculty:</span>
    <span>{{difDetail}}</span>
    <button v-show="buttonState"
            @click="doneButton">done!</button>
    <button @click='$emit("showEdit",itemIndex)'>edit</button>
    <button @click='$emit("remove")'>delete</button>
  </div>
</template>

<script>
export default {
  name: 'Todo-Item',
  props: ['itemIndex', 'todoDetail', 'freDetail', 'difDetail'],
  data() {
    return {
      buttonState: true,
    }
  },
  // created () {
  //   this.buttonState=true;
  // },
  methods: {
    doneButton() {
      this.$emit('doneTodo', difDetail);
      this.buttonState = false;
    }
  }
}

</script>


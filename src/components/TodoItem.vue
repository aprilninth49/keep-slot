<template>
  <div>
    <span>Todo:</span>
    <span>{{todoDetail}}</span>
    <span>Frequency:</span>
    <span>{{freDetail}}</span>
    <button v-show="buttonState"
            @click="doneButton">done!</button>
    <button @click='$emit("showEdit")'>edit</button>
    <button @click='$emit("remove")'>delete</button>
  </div>
</template>

<script>
export default {
  name: 'Todo-Item',
  props: ['todoDetail', 'freDetail'],
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
      this.$emit('doneTodo');
      this.buttonState = false;
    }
  }
}

</script>


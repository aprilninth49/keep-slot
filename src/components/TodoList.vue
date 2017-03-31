
<template>
  <div>
    <token-counter :number="tokenNumber"></token-counter>
    <button @click="showCreate=true">
      New Todo</button>
    <div v-show="showCreate">
      <label>Todo:</label>
      <input type="text"
             v-model='newItem.todo'></input>
      <label>Frequency:</label>
      <select v-model="newItem.frequency">
        <option value="everyday">everyday</option>
        <option value="everyweek">everyweek</option>
        <option value="onlyonce">onlyonce</option>
      </select>
      <label>Diffculty:</label>
      <select v-model="newItem.diffculty">
        <option value="easy">easy</option>
        <option value="normal">normal</option>
        <option value="hard">hard</option>
        <option value="hell">hell</option>
      </select>
      <button @click="createTodo">ok</button>
      <button @click="cancelTodo">cancel</button>
    </div>
    <!--<todo-create v-show="showCreate"
                                                                                       @createTodo="createTodo"
                                                                                       @cancelTodo="cancelTodo"></todo-create>-->
    <todo-edit v-show="editState"
               @hideEdit="hideEdit"
               @doneEdit="finishEdit"
               :item-index="editingIndex"
               :edit-todo="items[editingIndex].todo"
               :edit-frequency="items[editingIndex].frequency"></todo-edit>
    <todo-item v-for="(item, index) in items"
               :key="item.k"
               :todo-detail="item.todo"
               :fre-detail="item.frequency"
               :dif-detail="item.diffculty"
               :item-index="index"
               @doneTodo="doneTodo"
               @showEdit="showEdit"
               @remove="remove"></todo-item>
  </div>
</template>

<script>
import TokenCounter from './tokenCounter.vue'
import TodoItem from './TodoItem.vue'
// import TodoCreate from './TodoCreate.vue'
import TodoEdit from './TodoEdit.vue'
export default {
  name: 'list',
  components: {
    'token-counter': TokenCounter,
    'todo-item': TodoItem,
    // 'todo-create': TodoCreate,
    'todo-edit': TodoEdit
  },
  data() {
    return {
      tokenNumber: 0,
      showCreate: false,
      editState: false,
      k: 2,
      editingIndex: 0,
      newItem: {
        todo: '',
        frequency: 'onlyonce',
        diffculty: 'easy'
      },
      items: [
        {
          k: 0,
          todo: 'read news',
          frequency: 'everyday',
          diffculty: 'easy'
        },
        {
          k: 1,
          todo: 'clean litter box',
          frequency: 'everyweek',
          diffculty: 'normal'
        }
      ]
    }
  },
  //计算数组的长度，暂不需要
  // computed: {
  //   a() {
  //     return this.items.length
  //   }
  // },
  methods: {
    createTodo(item) {
      //原来的k值似乎可以去掉？
      // this.items.unshift(Object.assign({}, item, { k: this.k++ }));
      this.items.unshift(this.newItem);
      this.newItem = { todo: '', frequency: 'onlyonce' };
      this.showCreate = false;
    },
    cancelTodo() {
      this.newItem = { todo: '', frequency: 'onlyonce' };
      this.showCreate = false;
    },
    doneTodo(difDetail) {
      this.diffculty = difDetail;
      console.log(difDetail)
      if (this.diffculty = 'easy') {
        this.tokenNumber = this.tokenNumber + 1;
      } else if (this.diffculty = 'normal') {
        this.tokenNumber = this.tokenNumber + 2;
      } else if (this.diffculty = 'hard') {
        this.tokenNumber = this.tokenNumber + 3;
      } else {
        this.tokenNumber = this.tokenNumber + 4;
      }


      // return this.items.splice(index, this.items.length - index, this.items[index]);

    },
    showEdit(xxx) {
      this.editState = true;
      this.editingIndex = xxx;
    },
    hideEdit() {
      this.editState = false;
    },
    finishEdit(todo, frequency) {
      this.items[this.editingIndex].todo = todo;
      this.items[this.editingIndex].frequency = frequency;
      this.editState = false;

    },
    remove(index) {
      return this.items.splice(index, 1);
    }
  }
}
</script>


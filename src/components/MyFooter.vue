<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" v-model="isAll"/>
    </label>
    <span> <span>已完成 {{doneTotel}}</span> / 总共 {{ todos.length }} </span>
    <button class="btn btn-danger" @click="clean">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: "MyFooter",
  props: ["todos","checkAllTodo","clearnDoneTodo"],
  computed: {
    doneTotel() {
      return this.todos.reduce(
        (pre, current) => pre + (current.done ? 1 : 0),
        0
      );
    },
    isAll:{
      get(){
        return this.doneTotel === this.todos.length && this.todos.length > 0
        
      },
      set(done){
        this.checkAllTodo(done)
      }
    }
  },
  methods:{
    clean(){
      this.clearnDoneTodo()
    }
  }
};
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>
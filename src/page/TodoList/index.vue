<template>
  <div class="todoList">
    <div class="todoList_header">
      <input v-model="todoMessage" placeholder="add a todo"/>
      <button @click="addTodo">add</button>
    </div>
    <ul class="todoList_body">
      <li class="todoList-item" v-for="(item, index) in todoList" :key="index">
        {{item}}
        <button @click="removeTodo(index)">remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data () {
    return {
      todoMessage: '',
      todoList: [1, 2, 3]
    }
  },
  methods: {
    addTodo: function () {
      this.todoList.push(this.todoMessage)
      this.todoMessage = ''
    },
    removeTodo: function (index) {
      this.todoList = [].concat(this.todoList.slice(0, index), this.todoList.slice(index + 1))
    }
  }
}
</script>

<style scoped>
.todoList {
  width: 500px;
  margin: 0 auto;
}
.todoList_header {
  padding: 20px;
}

.todoList_body {
  list-style: none;
}

.todoList-item {
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
}

</style>

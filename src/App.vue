<template>
  <div>
    <h1>TodoList</h1>
    <TodoInput @add="onAddNewTask"></TodoInput>
    <TodoList :list="tasklist" class="mt-2"></TodoList>
    <TodoButton v-model:active="activeIndex"></TodoButton>
  </div>
</template>

<script>
import TodoList from "./components/todo-list/TodoList.vue"
import TodoInput from "./components/todo-input/TodoInput.vue"
import TodoButton from "./components/todo-button/TodoButton.vue"
export default {
  name: 'MyApp',
  data() {
    return {
      todolist: [
        { id: 1, task: '周一早餐9点开会', done: false },
        { id: 2, task: '周一晚上8点聚餐', done: false },
        { id: 3, task: '准备周三上午的演讲稿', done: true },
      ],
      nextId: 4,
      activeIndex: 0,
    }
  },
  methods: {
    onAddNewTask(task) {
      this.todolist.push({
        id: this.nextId, task: task, done: false
      });
      this.nextId += 1;
    }
  },
  components: {
    TodoList,
    TodoInput,
    TodoButton,
  },
  // 声明一个计算属性
  computed: {
    tasklist() {
      // 按需显示列表数据
      switch (this.activeIndex) {
        case 0:
          return this.todolist;

        case 1:
          return this.todolist.filter(x => x.done);

        case 2:
          return this.todolist.filter(x => !x.done);

      }
    }
  }
}
</script>

<style lang="less" scoped>
</style>

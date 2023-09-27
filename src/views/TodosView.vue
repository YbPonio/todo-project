<template>
  <div class="main">
    <h1>Create Todo</h1>
    <TodoCreator @create-todo="createTodo" />
    <ul class="todo-list" v-if="todoList.length > 0 ">
      <TodoItems v-for="(todo, index) in todoList" :todo="todo" :index="index" @toggle-complete="toggleTodoComplete"/>
    </ul>
    <p class="todos-msg" v-else>
      <span>You have no todos</span>
    </p>
  </div>
</template>

<script setup>
import TodoCreator from '../components/TodoCreator.vue';
import { ref } from 'vue';
import { uid } from 'uid';
import TodoItems from '../components/TodoItems.vue';

const todoList = ref([]);

const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isCompleted: false,
    esEditing: null,
  });
  console.log(todoList.value);
};

const toggleTodoComplete = (todoPos) => {
  todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted;
};
</script>

<style lang="scss" scoped>
.main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 16px;
}

.main h1 {
  margin-bottom: 16px;
  text-align: center;
}
.todo-list {
  display: flex;
  flex-direction: column;
  margin-top: 25px;
  gap: 10px;
}
.todos-msg {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}

</style>
<template>
    <div class="input-wrap" :class="{ 'input-err' : todoState.invalid }">
        <input type="text" v-model="todoState.todo" />
        <button @click="createTodo()">Create</button>
    </div>
    <p v-show="todoState.invalid" class="msg-err">{{ todoState.errMsg }}</p>
</template>

<script setup>
import { reactive, defineEmits } from 'vue';

const emit = defineEmits(["create-todo"]);

const todoState = reactive({
    todo: "",
    invalid: null,
    errMsg: "",
});

const createTodo = () => {
    todoState.invalid = null;
    if (todoState.todo !== ""){
        emit("create-todo", todoState.todo);
        todoState.todo = "";
        return;
    }
    todoState.invalid = true;
    todoState.errMsg = "Todo value must not be empty!";
};

</script>

<style lang="scss" scoped>
.input-wrap {
    display: flex;
    transition: 250ms ease;
    border: 2px solid #6d597a;

    &:focus-within {
        box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
    }
}
input {
    width: 100%;
    padding: 8px 6px;
    border: none;

    &:focus {
        outline: none;
    }
}

button {
    transition: all .2s ease-in;
    padding: 8px 16px;
    border: none;

    &:hover {
        background: #6D597A;
    }
}

.input-err {
    border-color: #ff0000;
}
.msg-err {
    color: #ff0000;
    font-size: 12px;
    text-align: center;
}
</style>
<template>
    <li>
        <input type="checkbox" :checked="todo.isCompleted" @input="$emit('toggle-complete', index)">
        <div class="todo">
            <input v-if="todo.isEditing" type="text" :value="todo.todo">
            <span v-else :class="{ 'completed-todo' : todo.isCompleted }">
                {{ todo.todo }}
            </span>
        </div>
        <div class="todo-actions">
            <Icon v-if="todo.isEditing" icon="ph:check-circle" class="icons" color="#0FFF50" width="25" />
            <Icon v-else icon="ph:pencil" class="icons" color="#0FFF50" width="25" />
            <Icon icon="ph:trash" class="icons" color="#FF3131" width="25" />
        </div>
    </li>
</template>

<script setup>
import { Icon } from '@iconify/vue';

const props = defineProps({
    todo: {
        type: Object,
        required: true,
    },
    index: {
        type: Number,
        required: true,
    }
});

defineEmits(["toggle-complete"]);
</script>

<style lang="scss" scoped>
li {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 16px 10px;
    background-color: #355070;
    box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.3),
    0 8px 10px -6px rgb(0 0 0 / .2);
    list-style-type: none;

    &:hover {
        .todo-actions {
            opacity: 1;
        }
    }
}

input[type="checkbox"] {
    appearance: none;
    width: 20px;
    height: 20px;
    background: #ffffff;
    border-radius: 50%;
    box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);

    &:checked {
        background-color: #B56576;
    }
}

.todo {
    flex: 1;
}

.todo input[type="text"] {
    width: 100%;
    padding: 2px 6px;
    border: 2px solid #6D597A;
}
.todo-actions {
    display: flex;
    gap: 6px;
    opacity: 0;
    transition: 150ms ease-in-out;
}
.todo-actions .icons {
    cursor: pointer;
}

.completed-todo {
    text-decoration: line-through;
}
</style>
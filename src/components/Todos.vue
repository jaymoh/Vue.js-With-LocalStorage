<template>
    <div class="card-body mb-2 list-group ml-3">
        <p class="card-text" v-if="!todo_items.length">Your Todo List is empty. Add something! </p>

        <div v-bind:key="todo_item.id" v-for="todo_item in todo_items" class="list-group-item mb-2">
            <TodoItem v-bind:todo_item="todo_item"></TodoItem>
        </div>
    </div>
</template>
<script>
import TodoItem from './TodoItem.vue';
    export default {
        name: "Todos",
        props: ["todo_items"],
        components: {
            TodoItem
        }
    }
</script>

<style scoped>

</style>
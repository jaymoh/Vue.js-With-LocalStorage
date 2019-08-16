<template>
    <div class="card-body mb-2 list-group ml-3">
        <p class="card-text" v-if="!todo_items.length">Your Todo List is empty. Add something! </p>

        <div v-bind:key="todo_item.id" v-for="todo_item in todo_items" class="list-group-item mb-2">
            <TodoItem v-bind:todo_item="todo_item" v-on:del-todo-item="delTodoMethod" v-on:mark-todo-item="markTodoMethod" v-on:edit-todo-item="editTodoMethod"></TodoItem>
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
        },
        methods: {
            delTodoMethod(id){
                //send to parent
                this.$emit('del-todo-event', id);
            },
            markTodoMethod(id){
                //send to parent
                this.$emit('mark-todo-event', id);
            },
            editTodoMethod(id){
                //send to parent
                this.$emit('edit-todo-event', id);
            }
        }
    }
</script>

<style scoped>

</style>
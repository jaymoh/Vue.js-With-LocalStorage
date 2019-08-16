<template>
    <div class="float-left">
        <span class="float-left custom-control custom-checkbox">
            <input type="checkbox" class="custom-control-input" v-bind:id="'id'+todo_item.id" v-on:change="$emit('mark-todo-item', todo_item.id)" v-if="todo_item.completed" checked/>
            <input type="checkbox" class="custom-control-input" v-bind:id="'id'+todo_item.id" v-on:change="$emit('mark-todo-item', todo_item.id)" v-else/>
            <label class="custom-control-label" v-bind:for="'id'+todo_item.id"></label>
        </span>
        <span class="float-right" v-bind:class="{'is-complete':todo_item.completed}">
            {{todo_item.title}}
            <i class="material-icons edit-icon" @click="$emit('edit-todo-item', todo_item.id)" v-if="!todo_item.completed">edit</i>
            <i class="material-icons del-icon" @click="$emit('del-todo-item', todo_item.id)">delete</i>
        </span>
    </div>
</template>

<script>
    export default {
        name: "TodoItem",
        props : ["todo_item"]
    }
</script>

<style scoped>
    .todo-item{
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .is-complete{
        text-decoration:line-through;
    }

    .del-icon{
        color: #bd2130;
        border-color: #b21f2d;
        vertical-align: middle;
        cursor: pointer;
    }
    .edit-icon{
        color: #117a8b;
        border-color: #10707f;
        vertical-align: middle;
        cursor: pointer;
        margin-left: 5px;
        margin-right: 10px;
    }
    .custom-checkbox{
        vertical-align: middle;

    }

</style>
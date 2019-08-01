,<template>
    <div class="todo-item" v-bind:class="{'is-completed':todo.completed}">
        <p>
          <input type="checkbox" v-on:change='markComplte'>    
            {{todo.title}}
            <button @click="$emit('del-todo',todo.id)" class="del">X</button>
            </p>
    </div>
</template>

<script>
import { METHODS } from 'http';
export default {
    name: "TodoItem",
    props:["todo"],
    methods: {
        markComplte() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>
 
<style scoped>

.todo-item {
    background:#f4f4f4;
    padding:10px;
    border-bottom: 1px #ccc dotted;
}

.is-completed {
    text-decoration: line-through;
}

.del {
    background: #ff0000;
    color:#fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
}
</style>


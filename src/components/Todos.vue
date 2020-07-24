<template>
    <div>
        <h1>Todos</h1>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <!-- <h4>{{todo.title}}</h4> -->
            <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
    name: "Todos",
    props: ["todos"],
    components: {
        TodoItem
    },
}
</script>


<style scoped>
h1 {
    color: red;
}

h4 {
    font-style: italic;
}
</style>
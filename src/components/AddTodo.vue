<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
import uuid from 'uuid';
export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            //stop the default behaviour
            //do not reload the page
            e.preventDefault();
            //!!install a package uuid
            //for generate random id
            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            }

            console.log(newTodo);
            //send it to parent
            this.$emit('add-todo', newTodo);

            //clear the input field
            this.title='';
        }
    }
}
</script>


<style scoped>
form {
    display:flex;
}
input[type="text"] {
    flex: 6;
    padding: 5px;
}

input[type="submit"] {
    flex: 1;
}
</style>
<template>
     <div class="todo-container">
          <div class="todo-item" :key="todo.id" v-for="todo in todos">
               <TodoItem
                    :todo="todo"
                    @listen-delete-task="$emit('listen-delete-task', todo.id)"
               />
          </div>
     </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
     name: "TodosList",
     props: {
          todos: Array,
     },
     components: {
          TodoItem,
     },
     emits: ["listen-delete-task"],
};
</script>
<style scoped>
.todo-container {
     width: 100%;
     display: flex;
     align-items: flex-start;
     justify-content: flex-start;
     flex-direction: column;
     box-sizing: border-box;
}
.todo-item {
     background: #dbdff0;
     width: 100%;
     padding: 10px;
     box-sizing: border-box;
     margin-bottom: 12px;
     position: relative;
     border-left: 5px solid green;
}
.todo-item:last-of-type {
     margin-bottom: 0px;
}
</style>

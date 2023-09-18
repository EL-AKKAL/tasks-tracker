<template>
     <div class="container">
          <AppHeader :text="textButton" @listen-toggle-form="setToggleForm" />
          <AppForm v-if="toggleForm" @listen-new-todo="addTodo" />
          <TodosList :todos="todos" @listen-delete-task="deleteTodo" />
          <AppFooter />
     </div>
</template>
<!-- //     "resolutions": { "eslint-loader": "2.1.2" }, -->
<script>
import AppHeader from "./components/AppHeader";
import AppForm from "./components/AppForm";
import TodosList from "./components/TodosList";
import AppFooter from "./components/AppFooter";

export default {
     name: "App",
     components: {
          AppHeader,
          AppForm,
          TodosList,
          AppFooter,
     },
     data() {
          return {
               todos: [],
               toggleForm: true,
               textButton: "Close",
          };
     },
     methods: {
          setToggleForm() {
               this.toggleForm = !this.toggleForm;
               this.textButton = this.textButton == "Open" ? "Close" : "Open";
          },
          deleteTodo(id) {
               if (confirm("are you sure you want to delete this task ? ")) {
                    this.todos = this.todos.filter((todo) => todo.id != id);
               }
          },

          async fetchTodos() {
               const response = await fetch("http://localhost:5000/todos");
               const data = await response.json();
               return data;
          },
          async fetchTodo(id) {
               const response = await fetch(`api/todos/${id}`);
               const data = await response.json();
               return data;
          },
     },
     async created() {
          this.todos = await this.fetchTodos();
     },
};
</script>

<style>
.container {
     display: flex;
     align-items: center;
     justify-content: center;
     flex-direction: column;
     border: 2px solid #b6aeea;
     width: 480px;
     margin: 0 auto;
     margin-top: 30px;
     padding: 0px 50px;
     border-radius: 7px;
}
h1,
h2,
h3,
h4,
h5,
h6,
label,
input,
footer,
p {
     color: #0f0b28;
     font-family: Tahoma;
     margin: 0;
}
button {
     background: #5442cd;
     color: #fff;
     cursor: pointer;
     padding: 6px 22px;
     border-radius: 7px;
     font-family: Tahoma;
     font-weight: 700;
     transition: 0.4s ease-in-out;
}
button:hover {
     background: #3b2ba1;
     color: #dbd7f4;
}
@media only screen and (max-width: 720px) {
     .container {
          width: 320px;
          padding: 0px 30px;
     }
}
</style>

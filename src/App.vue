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
          addTodo(todo) {
               this.todos = [...this.todos, todo];
          },
     },
     created() {
          this.todos = [
               {
                    id: 1,
                    task: "visit doctor",
                    dat: "Next Monday at 7am",
               },
               {
                    id: 2,
                    task: "football game",
                    dat: "13 march at 7pm",
               },
               {
                    id: 3,
                    task: "school exam",
                    dat: "first of july at 7am",
               },
               {
                    id: 4,
                    task: "project delivery",
                    dat: "22 june at 12am",
               },
               {
                    id: 5,
                    task: "cousin birthday",
                    dat: "the fifth of august",
               },
          ];
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

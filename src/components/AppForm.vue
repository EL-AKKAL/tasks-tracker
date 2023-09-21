<template>
     <div class="form">
          <div class="input-group">
               <label for="task">Task</label>
               <input
                    placeholder="ex : football game"
                    v-model="text"
                    type="text"
                    id="task"
                    name="task"
               />
          </div>
          <div class="input-group">
               <label for="dat">Day and Time</label>
               <input
                    @keyup.enter="addNewTodo"
                    placeholder="ex : the first of july"
                    v-model="dat"
                    type="text"
                    id="dat"
                    name="dat"
               />
          </div>
          <button @click="addNewTodo()" class="save">Save Task</button>
     </div>
</template>

<script>
export default {
     name: "AppForm",
     data() {
          return {
               text: "",
               dat: "",
          };
     },
     methods: {
          addNewTodo() {
               if (!this.text || !this.dat) {
                    alert("no inputs should be empty");
                    return;
               }
               const newTodo = {
                    task: this.text,
                    dat: this.dat,
               };
               this.text = "";
               this.dat = "";
               this.$emit("listen-new-todo", newTodo);
          },
     },
};
</script>

<style scoped>
.form {
     display: flex;
     align-items: flex-start;
     justify-content: flex-start;
     flex-direction: column;
     width: 100%;
     margin-bottom: 15px;
}
.input-group {
     display: flex;
     align-items: flex-start;
     justify-content: flex-start;
     flex-direction: column;
     margin-bottom: 12px;
     width: 100%;
}
label {
     margin-bottom: 7px;
     font-size: 18px;
}
label,
input {
     font-weight: 500;
}
input {
     font-size: 22px;
     padding: 3px 5px;
     width: 100%;
     box-sizing: border-box;
}
.save {
     background: #3b2ba1;
     width: 100%;
     font-weight: 900;
     font-size: 22px;
}
@media only screen and (max-width: 720px) {
     .save {
          font-size: 20px;
          font-weight: 600;
     }
     input {
          font-size: 18px;
          padding: 3px 5px;
          width: 100%;
          box-sizing: border-box;
     }
}
</style>

<template>
     <div>
          <XMarkIcon
               @click="$emit('listen-delete-task', todo.id)"
               class="icon-close"
          />
          <h4>{{ todo.task }}</h4>
          <p>{{ todo.dat }}</p>
     </div>
</template>

<script setup>
import { XMarkIcon } from "@heroicons/vue/24/outline";
</script>

<script>
export default {
     name: "TodoItem",
     props: { todo: Object },
};
</script>

<style scoped>
p {
     margin-top: 5px;
     font-size: 14px;
}
h4 {
     text-transform: capitalize;
}
.icon-close {
     width: 20px;
     height: auto;
     position: absolute;
     right: 7px;
     top: 7px;
     color: #4b5db4;
     cursor: pointer;
}
</style>

<template>
     <div class="inner-container">
          <h3>Todos Manager</h3>
          <button @click="$emit('listen-toggle-form')">{{ text }}</button>
     </div>
</template>

<script>
export default {
     name: "AppHeader",
     props: ["text"],
};
</script>

<style scoped>
.inner-container {
     width: 100%;
     display: flex;
     align-items: center;
     justify-content: space-between;
     gap: 60px;
     padding-top: 25px;
     padding-bottom: 25px;
}
h3 {
     font-size: 25px;
}
button {
     font-size: 16px;
}
@media only screen and (max-width: 720px) {
     h3 {
          font-size: 22px;
     }
}
</style>

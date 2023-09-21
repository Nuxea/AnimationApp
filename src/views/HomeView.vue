<script setup>

import {ref} from "vue";

const names = ref(["Selena Damo","Kevin Johnstone"])
const nameInput = ref("")

const addInvitee = () => {
  names.value.unshift(nameInput.value)
  nameInput.value = ""
}
</script>

<template>
  <main>
    <div class="container">
      <input v-model="nameInput" @keydown.enter="addInvitee" type="text" name="" id="" placeholder="Add person to invite...">
      <ul>
        <li v-for="name in names" :key="name">
          {{ name }}
        </li>
      </ul>
    </div>
  </main>
</template>

<style scoped>
.container {
  max-width: 300px;
  margin: 0 auto;
}

.container input {
  width: 100%;
  border-radius: 5px;
  border: 1px solid rgba(128,128,128,0.13);
  padding: 10px;
  margin: 20px auto;
  box-shadow: 1px 1px 10px rgba(0,0,0,1);
}

ul {
  display: inline;
  list-style: none;
  margin: 0;
  padding: 0;
}

li {
  list-style: none;
  width: 300px;
  border-radius: 5px;
  padding: 5px 10px;
  margin-top: 10px;
  background-color: #3b3b3b;
  box-shadow: 1px 1px 10px rgba(0,0,0,1);
  text-align: center;
  cursor: pointer;
}
</style>
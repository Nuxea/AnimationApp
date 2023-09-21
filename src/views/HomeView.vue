<script setup>

import {ref} from "vue";

const names = ref(["Selena Damo","Kevin Johnstone"])
const nameInput = ref("")

const addInvitee = () => {
  names.value.unshift(nameInput.value)
  nameInput.value = ""
}

const removeInvitee = (name) => {
  names.value = names.value.filter(n => n !== name)
}
</script>

<template>
  <main>
    <div class="container">
      <input v-model="nameInput" @keydown.enter="addInvitee" type="text" name="" id="" placeholder="Add person to invite...">
      <TransitionGroup name="invitees">
        <li v-for="name in names" :key="name" @click="removeInvitee(name)">
          {{ name }}
        </li>
      </TransitionGroup>
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

/* TRANSITION GROUP */
.invitees-enter-from {
  opacity: 0;
  transform: scale(0.5);
}

.invitees-enter-to {
  opacity: 1;
  transform: scale(1);
}

.invitees-enter-active {
  transition: all 0.5s ease;
}

.invitees-leave-from {
  opacity: 1;
  transform: scale(1);
}

.invitees-leave-to {
  opacity: 0;
  transform: scale(0);
}

.invitees-leave-active {
  transition: all 0.5s ease;
  position: absolute;
}

.invitees-move {
  transition: all 0.5s ease;
}
</style>
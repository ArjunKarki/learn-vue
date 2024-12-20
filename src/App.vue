<template>
  <h1>Hello {{ name }}</h1>
  <br />
  <form @submit.prevent="addTask">
    <label for="newTask">New Task</label>
    <input type="text" id="newTask" v-model="newTask" />
    <button>Add</button>
  </form>

  <p v-if="status === 'active'">You are active</p>
  <p v-else>You are inactive</p>
  <br />
  <button @click="toggleStatus">Toggle status</button>
  <br />
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      {{ task }}
      <span>
        <button @click="deleteTask(index)">X</button>
      </span>
    </li>
  </ul>
  <br />
  <a :href="link">Google</a>
</template>

<script setup>
import { onMounted, ref } from "vue";

const name = ref("Arjun Kari");
const status = ref("inactive");
const tasks = ref([]);
const link = ref("https://google.com");
const newTask = ref("");

const toggleStatus = () => {
  status.value = status.value === "active" ? "inactive" : "active";
};

const addTask = () => {
  if (newTask.value === "") return;
  tasks.value.push(newTask.value);
  newTask.value = "";
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};

onMounted(async () => {
  const res = await fetch("https://jsonplaceholder.typicode.com/todos");
  const resJson = await res.json();
  tasks.value = resJson.map((t) => t.title);
});
</script>

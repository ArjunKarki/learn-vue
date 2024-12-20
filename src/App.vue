<template>
  <h1>Hello {{ name }}</h1>
  <br />
  <p v-if="status === 'active'">You are active</p>
  <p v-else>You are inactive</p>
  <br />
  <button @click="toggleStatus">Toggle status</button>
  <br />
  <ul>
    <li v-for="task in tasks" :key="task">
      {{ task }}
    </li>
  </ul>
  <br />
  <a :href="link">Google</a>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const name = ref("Arjun Kari");
    const status = ref("inactive");
    const tasks = ref(["Learn Vue", "Initialize Vue", "Master Vue"]);
    const link = ref("https://google.com");

    const toggleStatus = () => {
      status.value = status.value === "active" ? "inactive" : "active";
    };

    return {
      name,
      status,
      tasks,
      link,
      toggleStatus,
    };
  },
};
</script>

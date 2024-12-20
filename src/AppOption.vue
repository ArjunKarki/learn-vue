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
export default {
  data() {
    return {
      name: "Arjun Kari",
      status: "inactive",
      tasks: ["Learn Vue", "Initialize Vue", "Master Vue"],
      link: "https://google.com",
    };
  },
  methods: {
    toggleStatus() {
      this.status = this.status === "active" ? "inactive" : "active";
    },
  },
};
</script>

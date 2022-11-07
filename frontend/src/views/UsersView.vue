<template>
  <div class="users">
    <h1>This is a users page</h1>
  </div>
  <ul>
    <template v-for="user in users.data" :key="user.id">
      <li>{{ user.firstName }} {{ user.lastName }}</li>
    </template>
  </ul>
</template>

<script setup>
// COMPOSITION API
import { onMounted, reactive } from "vue";
import http from "@/services/http.js";

let users = reactive({ data: [] });

onMounted(async () => {
  try {
    const { data } = await http.get("api/users");
    users.data = data;
  } catch (error) {
    console.log(error);
  }
});

// OPTIONS API
// import http from "@/services/http.js";
// export default {
//   data() {
//     return {
//       users: [],
//     };
//   },
//   async mounted() {
//     try {
//       const { data } = await http.get("http://localhost:8000/api/users");
//       this.users = data;
//     } catch {
//       console.log(error);
//     }
//   },
// };
</script>

<template>
  {{ count }}
  <div v-if="showHeader">
    <Header />
  </div>
  <button v-on:click="showHeader = !showHeader">Toggle Header</button>
  <ul>
    <li v-for="user in users">{{ user.name }} - {{ user.age }}</li>
  </ul>
  <div>
    <router-link to="/"> Home </router-link>
    <router-link to="/products"> Produtos </router-link>
    <router-link to="/about"> Sobre </router-link>
  </div>
  <div>
    <router-view></router-view>
  </div>
  <Footer />
</template>

<script setup>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import { onMounted, reactive, ref } from "vue";

// *** COMPOSITION API WITH "SCRIPT SETUP" ***
const count = ref(0);
const showHeader = ref(false);
const users = reactive([
  {
    name: "Paulo Lobo",
    age: 52,
  },
  {
    name: "Luiz Barreto",
    age: 43,
  },
]);

function add() {
  count.value++;
}

onMounted(() => {
  console.log(users);
});

// *** COMPOSITION API ***
// export default {
//   components: { Header, Footer },
//   setup() {
//     const count = ref(0);

//     function add(){
//       count.value++
//     }

//     return {
//       count, add
//     }
//   }
// }

// *** OPTIONS API ***
// export default {
//   components: { Header, Footer },
//   data() {
//     return {
//       count: 0
//     }
//   },
//   methods: {
//     add() {
//       this.count++
//     }
//   }
// }
</script>

<style scoped></style>

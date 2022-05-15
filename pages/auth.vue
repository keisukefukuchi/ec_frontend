<template>
  <div class="container">
    <div class="header">
      <Header></Header>
    </div>
    <div class="auth-container">
      <Login></Login>
      <Register></Register>
    </div>
  </div>
</template>



<script>
import Header from "../components/Header.vue";
import Register from "../components/Register.vue";
import Login from "../components/Login.vue";

import '@/assets/css/auth.css'

export default {
  components: {
    Header,
    Register,
    Login,
  },
};
</script>

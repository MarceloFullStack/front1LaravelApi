<template>
  <ul>
    <li>
      <h1 v-if="user">Bem vindo {{ user.name }}</h1>

      <template v-if="authenticated">
        <router-link :to="{ name: 'Home' }">HOME | </router-link>
        <a href="#" @click.prevent="LogOut" rel="noopener noreferrer">SigOut</a>
        <router-link :to="{ name: 'Dashboard' }"> DashBoard</router-link>
      </template>

      <!-- <template v-else>
        <router-link :to="{ name: 'Login' }"> LOGIN |</router-link>
      </template> -->
    </li>
  </ul>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
  computed: {
    //001 pegar dados do state
    ...mapGetters({
      user: "auth/user",
      authenticated: "auth/authenticated",
    }),
  },
  methods: {
       ...mapActions({
        LogOutAction:'auth/LogOut'
    }),
    LogOut(){
        this.LogOutAction().then(()=>{
            this.$router.replace({
                name:'Login'
            })
        })
    }
  },
};
</script>

<style>
h1{
    text-align: center;
}
ul {
  list-style: none;
}
</style>

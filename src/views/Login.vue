<template>
  <form @submit.prevent="submit" method="POST">
    <div>
      <label for="email"> email </label>
      <input type="text" name="email" id="email" v-model="form.email" />
      <br />
      <label for="password"> password </label>
      <input
        type="password"
        name="password"
        id="password"
        v-model="form.password"
      />
    </div>
    <button type="submit">Enviar</button>
  </form>
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "login",
  comments: {},
  methods: {
    ...mapActions({
      login: "auth/login",
      attempt: "auth/attempt",
    }),
     submit() {
      this.login(this.form)
    },
    alert() {
      this.attempt;
    },
  },
  data() {
    return {
      form: {
        email: "",
        password: "",
      },
    };
  },
};
</script>

<style>
</style>

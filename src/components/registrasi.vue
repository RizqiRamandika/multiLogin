<template>
  <div class="kotak_login">
    <p class="tulisan_login">Silahkan Registrasi</p>
    <form>
      <label>Username</label>
      <input
        type="text"
        name="username"
        v-model="username"
        class="form_login"
        placeholder="Username atau email .."
      />
      <br />
      <label>Password</label>
      <input
        type="password"
        name="password"
        v-model="password"
        class="form_login"
        placeholder="Password .."
      /><br />

      <div
        @click="login"
        style="
          background: #46de4b;
          color: white;
          text-align: center
          font-size: 11pt;
          width: 100%;
          border: none;
          border-radius: 3px;
          padding: 10px 20px;
        "
      >
        <bottom>REGISTER</bottom>
      </div>

      <br />
      <br />
    </form>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "login",
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    async login() {
      const payload = {
        username: this.username,
        password: this.password,
        role: "siswa",
      };
      await axios.post("http://localhost:3000/users", payload);
      this.$router.push("/");
    },
  },
};
</script>
<template>
  <div class="kotak_login">
    <p class="tulisan_login">Silahkan Registrasi</p>
    <form>
      <label>Username</label>
      <input
        type="text"
        name="username"
        v-model="username"
        required
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
        required
        placeholder="Password .."
      /><br />

      <input type="button" @click="reg()" class="tombol_login" value="REGISTER" />

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
    async reg() {
      const payload = {
        username: this.username,
        password: this.password,
        role: "siswa",
      };
      if (payload.username === "") {
        alert("Username tidak boleh kosong");
      } else if (payload.password === "") {
        alert("password tidak boleh kosong");
      } else {
        await axios.post("http://localhost:3000/users", payload);
        this.$router.push("/");
      }
    },
  },
};
</script>
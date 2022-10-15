<template>
  <div id="App">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" href="/navbar">Rizqi</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active">
            <a class="nav-link" href="/"
              >Home <span class="sr-only">(current)</span></a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/link">Link</a>
          </li>
        </ul>
        <form class="form-inline my-2 my-lg-0">
          <a
            href="/login"
            v-if="logout === null"
            class="btn btn-outline-success my-2 my-sm-0"
          >
            Log In
          </a>
          <a
            href="/"
            v-if="logout !== null"
            @click="out"
            class="btn btn-outline-success my-2 my-sm-0"
          >
            Log Out
          </a>
        </form>
      </div>
    </nav>
    <router-view></router-view>
  </div>
</template>
<script>
export default {
  name: "App",
  computed: {
    logout() {
      return JSON.parse(localStorage.getItem("USER_DATA"));
    },
  },
  methods: {
    out() {
      localStorage.clear();
    },
  },
};
</script>
<template>
  <div class="header">
    <router-link to="/" class="logo">HangoutMe</router-link>
    <div class="header-right">
      <router-link v-if="!this.$store.state.user.isLoggedIn" to="/signup" class="active">Sign up</router-link>
      <a v-else @click="onLogout">Log out</a>
    </div>
  </div>
</template>

<script>

import { LOG_OUT_USER } from "../mutation-types"
import router from '../router';

export default {
  name: "Header",
  data() {
    return {
      log_out: LOG_OUT_USER,
    };
  },
  methods: {
    onLogout () {
      router.push("/signup")
      this.$store.commit(this.log_out)
    }
  }
}



</script>

<style scoped>
.header {
  overflow: hidden;
  background-color: #f1f1f1;
  padding: 20px 10px;
}

/* Style the header links */
.header a {
  float: left;
  color: black;
  text-align: center;
  padding: 12px;
  text-decoration: none;
  font-size: 18px;
  line-height: 25px;
  border-radius: 4px;
  cursor: pointer;
}

/* Style the logo link (notice that we set the same value of line-height and font-size to prevent the header to increase when the font gets bigger */
.header a.logo {
  font-size: 25px;
  font-weight: bold;
}

/* Change the background color on mouse-over */
.header a:hover {
  background-color: #ddd;
  color: black;
}

/* Style the active/current link*/
.header a.active {
  background-color: dodgerblue;
  color: white;
}

/* Float the link section to the right */
.header-right {
  float: right;
}

/* Add media queries for responsiveness - when the screen is 500px wide or less, stack the links on top of each other */
@media screen and (max-width: 500px) {
  .header a {
    float: none;
    display: block;
    text-align: left;
  }

  .header-right {
    float: none;
  }
}
</style>

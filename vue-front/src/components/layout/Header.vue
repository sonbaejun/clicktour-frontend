<template>
  <nav>
    <v-toolbar
      dense
      style="
        height: 55px;
        top: 0px;
        margin-bottom: 35px;
        position: fixed;
        width: 100%;
        z-index: 1000000;
      "
    >
      <img
        src="../../assets/image 4.png"
        style="
          margin-left: 10px;
          margin-right: 2px;
          margin-top: 5px;
          border-radius: 10px;
          cursor: pointer;
          height: 45px;
          width: 42px;
        "
        @click="goHome"
      />
      <v-toolbar-title
        class="headerTitle"
        style="
          color: #1bc6ec;
          margin-top: 3px;
          cursor: pointer;
          font-family: 'Inter';
          font-style: normal;
          font-weight: 700;
        "
        @click="goHome"
        >ClickTour</v-toolbar-title
      >

      <v-spacer></v-spacer>
      <h4
        style="
          color: #1bc6ec;
          margin-top: 3px;
          margin-right: 5px;
          font-family: 'Inter';
          font-style: normal;
          font-weight: 700;
        "
      >
        {{ $store.state.userInfo.nickname }}
      </h4>
      <div style="margin-top: 3px" v-if="$store.state.token != null">
        <!-- <v-btn
          color="warning"
          fab
          dark
          style="height: 37px; width: 37px; margin-top: 3px"
        ></v-btn> -->
        <v-btn
          class="loginBtn"
          style="
            height: 37px;
            width: 37px;
            margin-right: 15px;
            border-radius: 8px;
            background-color: #1bc6ec;
            color: aliceblue;
            font-size: 12px;
            font-family: 'Inter';
            font-style: normal;
            font-weight: 700;
          "
          @click="goLogin"
          >Logout</v-btn
        >
      </div>
      <div style="margin-top: 3px" v-else>
        <v-btn
          color="warning"
          fab
          dark
          style="height: 37px; width: 37px; margin-top: 3px"
        ></v-btn>
        <v-btn
          class="loginBtn"
          style="
            height: 37px;
            width: 37px;
            margin-right: 15px;
            border-radius: 8px;
            background-color: #1bc6ec;
            color: aliceblue;
            font-size: 12px;
            font-family: 'Inter';
            font-style: normal;
            font-weight: 700;
          "
          @click="goLogin"
          >Login</v-btn
        >
      </div>
    </v-toolbar>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      loginBtn: "Login",
    };
  },
  methods: {
    goHome() {
      this.$router.push("/").catch(() => {});
    },
    goLogin() {
      if (this.$store.state.token != null) {
        localStorage.removeItem("userInfo");
        localStorage.removeItem("access_token");
        this.$store.commit("inituserInfo");
        this.$store.commit("initToken");
        this.$router.push("/").catch(() => {});
      } else {
        this.$router.push("/login").catch(() => {});
      }
    },
  },
};
</script>


<style scoped>
</style>
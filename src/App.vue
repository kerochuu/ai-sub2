<template>
  <v-app>
    <Header :user="user" />
    <Scroll />
    <v-content id="content">
      <router-view :user="user" />
    </v-content>
    <Footer />
  </v-app>
</template>

<script>
import store from "./store";
import Header from "./components/Header";
import Footer from "./components/Footer";
import Scroll from "./components/Scroll";
import FirebaseService from "./services/FirebaseService";

<<<<<<< HEAD

if (!window.chrome || navigator.userAgent.indexOf("Edge") !== -1 || navigator.userAgent.indexOf("OPR") !== -1 || navigator.userAgent.indexOf("Version") !== -1) {
  alert("이 사이트는 크롬에 최적화 되어 있읍니다. 크롬을 깔아주세욥");
=======
if (
  !window.chrome ||
  navigator.userAgent.indexOf("Edge") !== -1 ||
  navigator.userAgent.indexOf("OPR") !== -1 ||
  navigator.userAgent.indexOf("Version") !== -1
) {
  alert("이 사이트는 크롬에 최적화 되어 있읍니다. 크롬을 깔아주세욥");
} else {
  console.log("크롬임");
>>>>>>> origin/tyki
}

export default {
  name: "App",
  store,
  data() {
    return {
      user: ""
    };
  },
  components: {
    Header,
    Footer,
    Scroll
  },
  mounted() {
    FirebaseService.signout();
    FirebaseService.addPageLog(null);
    this.$router.push("/pass");
  },
  watch: {
    $route() {
      this.user = FirebaseService.getUserInfo();

      if (this.user) {
        var id = this.user.uid;
      } else {
        var id = "unauthenticated";
      }
      FirebaseService.addPageLog(id);
    }
  }
};
</script>

<style>
@media screen and(max-width:48px) {
  #content {
    margin-top: 48px;
  }
}

@media screen and(max-width:56px) {
  #content {
    margin-top: 56px;
  }
}
@media screen and(max-width:1092) {
  #content {
    margin-top: 64px;
  }
}
</style>

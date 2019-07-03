<template>
  <v-app>
    <Header />
    <v-content id="content">
      <router-view />
    </v-content>
    <Footer />
  </v-app>
</template>

<script>
import store from "./store";
import Header from "./components/Header";
import Footer from "./components/Footer";

export default {
  name: "App",
  store,
  data() {
    return {
      //
    };
  },
  components: {
    Header,
    Footer
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

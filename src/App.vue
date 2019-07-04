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

if(!window.chrome){
  // firefox
  alert('이 사이트는 크롬에 최적화 되어 있읍니다. 크롬을 깔아주세욥');
} else {
  if (navigator.userAgent.indexOf('Edge')!==-1 || navigator.userAgent.indexOf('OPR')!==-1 || navigator.userAgent.indexOf('Version')!==-1) {
    alert('이 사이트는 크롬에 최적화 되어 있읍니다. 크롬을 깔아주세욥');
  } else { 
    console.log('크롬임');
  }
}

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

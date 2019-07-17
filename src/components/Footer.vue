<template>
  <div>
    <footer>
      <strong>@ 이주원과아이들 - 2019</strong>
      <div id="snsIcon">
        <div>
          <strong class="mr-3">Contact Us</strong>
          <a href="https://lab.ssafy.com/zooo1/webmobile-sub2/">
            <v-icon size="30" class="mr-3" style="color:white;">fa-github</v-icon>
          </a>
          <router-link to="#">
            <v-icon size="30" style="color:white;">fa-facebook-square</v-icon>
          </router-link>
        </div>
      </div>
    </footer>
    <!-- 날씨 정보 -->
    <weather></weather>
    <div id="translate">
      <Translate></Translate>
    </div>
  </div>
</template>

<script>
import weather from "@/components/weather.vue";
import Translate from "./Translate.vue";

export default {
  name: "Footer",
  components: {
    weather,
    Translate
  }
};
</script>

<style scoped>
div {
  background-color: #333;
  /* background-image: linear-gradient(to bottom right, #E39B82, #FEF3CB); */
}
footer {
  font-family: "Montserrat", sans-serif;
  color: #f0f0f0;
  font-size: 20px;
  font-weight: 700;
  padding: 15px;
}
a {
  text-decoration: none;
}
strong {
  margin: 0 3;
}
#snsIcon {
  color: #f0f0f0;
  float: right;
}
#translate {
  float: right;
  margin: 20px 120px;
  /* right: 20px; 
  bottom: 20px; */
  /* float: right; */
}
</style>

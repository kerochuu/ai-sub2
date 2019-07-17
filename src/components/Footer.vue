<template>
  <div>
  <footer>
    <strong>@이주원과아이들 - 2019.07.08</strong>
    <div id="snsIcon">
      <strong class="mr-3">Contact Us</strong>
      <a href="https://lab.ssafy.com/zooo1/webmobile-sub2/"><v-icon size="30" class="mr-3">fa-github</v-icon></a>
      <router-link to="#"><v-icon size="30">fa-facebook-square</v-icon></router-link>
    </div>
  </footer>
  <!-- 날씨 정보 -->
  <weather></weather>
</div>
</template>

<script>
import weather from '@/components/weather.vue'

export default{
  name: "Footer",
  components:{
    weather
  }
}
</script>

<style scoped>
div{
    background-color: rgb(182, 133, 90);
}
footer{
  font-family: 'Montserrat', sans-serif;
  font-size: 20px;
  font-weight: 700;
  padding: 15px;

}
a {
  text-decoration: none;
}
strong{
  margin: 0 3;
}
#snsIcon{
  color: #333;
  float:right;
}

</style>

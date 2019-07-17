<template>
  <div>
    <!-- <ImgBanner imgSrc="https://source.unsplash.com/5brvJbR1Pn8/1600x900">
      <div style="line-height:1.2em;font-size:1.2em;" slot="text">Portfolio</div>
    </ImgBanner>-->
    <v-container>
      <div>
        <h1>Portfolio Page</h1>
      </div>
      <!-- Portfolio -->
      <v-layout>
        <v-flex xs12>
          <PortfolioList :limits="4" :load-more="true"></PortfolioList>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import ImgBanner from "../components/ImgBanner";
import PortfolioList from "../components/PortfolioList";

export default {
  name: "PortfolioPage",
  components: {
    ImgBanner,
    PortfolioList
  }
};
</script>
<style scoped>
h1{
  margin-top: 80px;
  text-align:center;
}
</style>

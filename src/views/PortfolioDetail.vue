<template>
  <v-container>
    <v-layout wrap row>
      <img id="portfolioImg" :src="portfolio.img">
      <div class="information">
        <h1>{{portfolio.title}}</h1>
        <hr style="margin-top:1px;">
        <h2>{{portfolio.created_at}}</h2>
        <p>{{portfolio.body}}</p>
      </div>
    </v-layout>
  </v-container>
</template>

<script>
import FirebaseService from "@/services/FirebaseService";

export default {
  name: "PortfolioDetail",
  data() {
    return {
      portfolio: {},
      pid: ""
    };
  },

  methods: {
    getInfo: function() {
      this.pid = this.$route.params.pid;
    }
  },
  mounted() {
    this.getInfo();
    FirebaseService.getPortfolioById(this.pid).then(res => {
      this.portfolio = res[0];
    });
    console.log(this.created_at);
  }
};
</script>

<style scoped>
#portfolioImg {
  display: block;
  margin: 10vh 15%;
  width: 70%;
  height: 50%;
}
.containerBox {
  margin: 10vh 10vw 0 10vw;
}

.information{
  font-family: 'Montserrat', sans-serif;
  margin: 0 15%;

}

</style>

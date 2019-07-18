<template>
  <div id="Portfolio">
    <v-container>
      <div>
        <h1 style="text-align:center; font-size:8vh;">Portfolio Page</h1>
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
import PortfolioList from "../components/PortfolioList";

export default {
  name: "PortfolioPage",
  components: {
    PortfolioList
  }
};
</script>

<style>
#Portfolio{
  margin: 100px 0px;
}
</style>

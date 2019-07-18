<template>
  <v-card id="portfolioCard">
    <router-link :to="{name:'portfolioDetail', params: {pid} }">
      <v-img :src="imgSrc" height="200px"></v-img>
    </router-link>
    <v-card-title primary-title>
      <div>
        <div id="title" class="headline">{{title}}</div>
        <span id="content" class="grey--text">{{body}}</span>
      </div>
    </v-card-title>
  </v-card>
</template>

<script>
export default {
  name: "Portfolio",
  props: {
    date: { type: String },
    title: { type: String },
    body: { type: String },
    imgSrc: { type: String },
    pid: { type: String }
  },
  data() {
    return {
      //
    };
  }
};
</script>

<style scoped>
#portfolioCard{
  border-radius: 4px;
  border: 5px solid #2D0E0E;
}
#title {
  font-family: 'Montserrat', sans-serif !important;
  font-weight: bold;
  width: 150px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
#content {
  font-family: 'Montserrat', sans-serif !important;
  font-size: 16px;
  display: -webkit-box;
  -webkit-line-clamp: 1;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>

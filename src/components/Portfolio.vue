<template>
  <v-card>
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
#title {
  width: 150px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
#content {
  display: -webkit-box;
  -webkit-line-clamp: 1;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>

<template>
  <div>
    <v-container>
      <!-- Post -->
      <v-layout>
        <v-flex sm12>
          <PostList :limits="3" :load-more="true"></PostList>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import ImgBanner from "../components/ImgBanner";
import PostList from "../components/PostList";

export default {
  name: "PostPage",
  components: {
    ImgBanner,
    PostList
  }
};
</script>

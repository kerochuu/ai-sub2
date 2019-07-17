<template>
  <div>
    <i class="fas fa-pencil-alt"></i>
    <!-- <div v-on:click="changeBannerImg"> -->
      <!-- <ImgBanner v-bind:imgSrc="img"> -->
      <ImgBanner> 
        <!-- <div id="introduce" style="line-height:1.2em; " slot="t  ext">TEAM AVOCADO</div> -->
      </ImgBanner>
    <!-- </div> -->

    <v-container>
      <!-- Portfolio -->
      <v-layout my-5>
        <v-flex xs12>
          <h2 class="headline my-5 text-xs-center">About us</h2>
          <PortfolioList></PortfolioList>
        </v-flex>
      </v-layout>

      <!-- Post -->
      <!-- <v-layout my-5>
        <v-flex xs12>
          <h2 class="headline my-5 text-xs-center">Post</h2>
          <PostList :column="1"></PostList>
        </v-flex>
      </v-layout> -->

      <!-- Github -->
      <v-layout my-5>
        <v-flex xs12>
          <h2 class="headline my-5 text-xs-center">Project</h2>
          <RepositoryList></RepositoryList>
        </v-flex>
      </v-layout>

      <!-- translate -->
      <!-- <v-layout>
        <v-flex>
          <Translate></Translate>
        </v-flex>
      </v-layout> -->
    </v-container>
  </div>
</template>

<script>
import ImgBanner from "../components/ImgBanner";
import PortfolioList from "../components/PortfolioList";
import PostList from "../components/PostList";
import RepositoryList from "../components/RepositoryList";
import ImageUpload from "../components/ImageUpload";
import Translate from "../components/Translate";

export default {
  name: "HomePage",
  data() {
    return {
      showPhoto: false,
      randomImg: "https://picsum.photos/1080/1920",
      img: "https://picsum.photos/1080/1920"
    };
  },
  components: {
    ImgBanner,
    PortfolioList,
    PostList,
    RepositoryList,
    ImageUpload,
    Translate
  },
  methods: {
    // getImgUrl(img) {
    //   return require("../assets/" + img);
    // },
    // changeBannerImg() {
    //   this.showPhoto = !this.showPhoto;
    //   if (this.showPhoto && this.user.photoURL) {
    //     this.img = this.user.photoURL;
    //   } else {
    //     this.img = this.randomImg;
    //   }
    // }
  },
  props: ["user"]
};
</script>

<style scoped>
h2 {
  font-size: 3rem;
}

@media screen and (max-width: 1904px) {
  #aboutMe {
    font-size: 25px;
  }
}

@media screen and (max-width: 760px) {
  #aboutMe {
    font-size: 20px;
  }
}
#introduce {
  font-size: 45px;
  font-weight: bold;
  color: #f0f0f0;
  /* opacity: 1; */
}
</style>

<template>
<v-layout mt-5 wrap>
  <v-flex xs12>
    <ImgBanner imgSrc="https://source.unsplash.com/5brvJbR1Pn8/1600x900">
      <div style="line-height:1.2em;font-size:1.2em;" slot="text">Write your Portfolio</div>
    </ImgBanner>
  </v-flex>

  <v-flex xs12>
    <v-text-field label="Portfolio title" placeholder="Portfolio title" outline v-model="title"></v-text-field>
  </v-flex>

  <v-flex xs6>
    <v-textarea auto-grow="true" outline name="Portfolio Description" label="Portfolio Description" v-model="body" @input="update"></v-textarea>
  </v-flex>
  <v-flex xs6>
    <div v-html="compiledMarkdown"></div>
  </v-flex>

  <v-flex xs6>
    <ImageUpload ref="imgUpload" />
  </v-flex>
  <v-flex xs12 text-xs-center round my-5>
    <v-btn color="info" dark v-on:click="postPortfolios">
      <v-icon size="25" class="mr-2">fa-plus</v-icon>
      작성하기
    </v-btn>
  </v-flex>
</v-layout>
</template>

<script>
import ImageUpload from '@/components/ImageUpload'
import FirebaseService from '@/services/FirebaseService'
import ImgBanner from "../components/ImgBanner"
export default {
  name: 'PortfolioWrite',
  props: {
    title: {
      type: String,
      default: "title test"
    },
    body: {
      type: String,
      default: "# body test"
    },
    img: {
      type: String,
      default: ""
    },
  },
  components: {
    ImageUpload,
    ImgBanner
  },
  data() {
    return {
      file: '',
      description: "The Woodman set to work at once, and so sharp was his axe that the tree was soon chopped nearly through."
    }
  },
  methods: {
    async postPortfolios() {
      this.img = await this.$refs.imgUpload.imageUpload();
      FirebaseService.postPortfolio(this.title, this.body, this.img)
      this.$router.push({
        name: 'portfolio'
      })
    }
  }
};
</script>

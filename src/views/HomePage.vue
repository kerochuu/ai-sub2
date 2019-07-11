<template>
  <div>
    <i class="fas fa-pencil-alt"></i>
    <ImgBanner imgSrc="https://picsum.photos/1080/1920">
      <div id="introduce" style="line-height:1.2em;" slot="text">Do u love Avocado?<br>Do u love Avocado?</div>
    </ImgBanner>
    <v-container>
      <!-- About Me -->
      <v-layout  my-5>
        <v-flex id="aboutMe" sm12>
          <h2 class="headline mb-3 text-sm-center">About Me</h2>
          <p  class="mr-4 text-sm-center">안녕하세요, 서울 SSAFY 1기 이주원입니다.<br/>아보카도 좋아하세요?</p>
        </v-flex>
        <v-flex id="profileImg" md4>
          <v-img :src="getImgUrl('avocado.jpeg')" aspect-ratio="1.5"/>
        </v-flex>
      </v-layout>

      <!-- Portfolio -->
      <v-layout my-5>
        <v-flex xs12>
          <h2 class="headline my-5 text-xs-center">Portfolio</h2>
          <PortfolioList></PortfolioList>
        </v-flex>
      </v-layout>

      <!-- Post -->
      <v-layout my-5>
        <v-flex xs12>
          <h2 class="headline my-5 text-xs-center">Post</h2>
          <PostList :column="1"></PostList>
        </v-flex>
      </v-layout>


      <!-- Github -->
      <v-layout my-5>
        <v-flex xs12>
          <h2 class="headline my-5 text-xs-center">Project</h2>
          <RepositoryList></RepositoryList>
        </v-flex>
      </v-layout>

      <!-- Image Upload -->
      <v-layout>
        <v-flex>
          <ImageUpload></ImageUpload>
        </v-flex>
      </v-layout>

      <!-- google translate -->
      <v-layout>
        <v-flex>
          <Translate></Translate>
        </v-flex>
      </v-layout>
      
    </v-container>
  </div>
</template>

<script>
import ImgBanner from '../components/ImgBanner'
import PortfolioList from '../components/PortfolioList'
import PostList from '../components/PostList'
import RepositoryList from '../components/RepositoryList'
import ImageUpload from '../components/ImageUpload'
import Translate from '../components/Translate'

export default {
	name: 'HomePage',
	components: {
		ImgBanner,
		PortfolioList,
		PostList,
    RepositoryList,
    ImageUpload,
    Translate
	},
	methods: {
		getImgUrl(img) {
			return require('../assets/' + img)
		}
	},
}
</script>

<style scoped>


@media screen and (max-width: 1904px){
  #aboutMe{
    font-size: 25px;
  }
}

@media screen and (max-width: 760px){
  #profileImg{
    display: none;
  }
  #aboutMe{
    font-size: 20px;
  }
}
#introduce{
  font-size: 45px;
  font-weight: bold;
  color: black;
  opacity: 1;
}

</style>

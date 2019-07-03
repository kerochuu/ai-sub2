<template>
  <div>
    <i class="fas fa-pencil-alt"></i>
    <ImgBanner imgSrc="https://picsum.photos/1080/1920">
      <div style="line-height:1.2em;" slot="text">개발을 잘 하고 싶어요<br>~~</div>
    </ImgBanner>
    <v-container>
      <!-- About Me -->
      <v-layout  my-5>
        <v-flex id="aboutMe" sm12>
          <h2 class="headline mb-3 text-sm-center">About Me</h2>
          <p  class="mr-4 text-sm-center">안녕하세요, 서울 SSAFY 1기 이주원입니다.<br/>Vue를 열심히 공부해서 예쁜 블로그를 만들어보려고 노력 중입니다.</p>
        </v-flex>
        <v-flex id="profileImg" md4>
          <v-img :src="getImgUrl('profile.png')" aspect-ratio="1.5"/>
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
    </v-container>
  </div>
</template>

<script>
import ImgBanner from '../components/ImgBanner'
import PortfolioList from '../components/PortfolioList'
import PostList from '../components/PostList'
import RepositoryList from '../components/RepositoryList'

export default {
	name: 'HomePage',
	components: {
		ImgBanner,
		PortfolioList,
		PostList,
		RepositoryList
	},
	methods: {
		getImgUrl(img) {
			return require('../assets/' + img)
		}
	},
}
</script>

<style scoped>
@media screen and (max-width: 760px){
  #profileImg{
    display: none;
  }
}

#aboutMe{
  font-size: 1.5vw;
}

</style>

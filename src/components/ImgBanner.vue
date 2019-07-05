<template>
  <div>
    <v-img id="bannerImg" :src="imgSrc"
           aspect-ratio="1.7">
      <v-layout  align-center justify-center row fill-height>
        <v-flex text-xs-center>
          <span class="text-shadow display-2 font-weight-light">
            <slot name="text"/>
          </span>
        </v-flex>
      </v-layout>
    </v-img>
  </div>
</template>



<script>

export default {
	name: 'ImgBanner',
	props: {
		imgSrc: {type: String},
		text: {type: String}
	},
	methods: {
	},
}
</script>
<style>
  .text-shadow {
    text-shadow: 0 0 15px rgb(255,255,255);
  }

  @media screen and (max-width: 760px){
    #bannerImg{
      height: 100vh;
    } 
  }
  @media screen and(max-width: 1920px){
    #bannerImg{
      margin-top: 64px;
    }
  }
  
  @media screen and(max-width: 1920px){
    #bannerImg{
      margin-top: 64px;
    }
  }
  @media screen and(max-width: 960px){
    #bannerImg{
      margin-top: 48px;
    }
  }
   @media screen and(max-width: 600px){
    #bannerImg{
      margin-top: 64px;
    }
  }
  
  




</style>

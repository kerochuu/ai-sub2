<template>
  <v-app>
    <Header/>
    <v-content style="margin-top:70px;">
      <router-view/>
    </v-content>
    <Footer/>

  </v-app>
</template>

<script>
import store from './store'
import Header from './components/Header'
import Footer from './components/Footer'

export default {
	name: 'App',
	store,
	data() {
		return {
			//
		}
	},
  components: {
    Header,
    Footer
  }
}
</script>

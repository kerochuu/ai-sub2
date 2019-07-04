<template>
    <v-layout> 
        <p>{{portfolio.created_at}}</p>
        <p>{{portfolio.body}}</p>
        <p>{{portfolio.title}}</p>
        <img :src="portfolio.img" />
    </v-layout>
</template>

<script>
import FirebaseService from '@/services/FirebaseService'

export default {
    name : "PortfolioDetail",
    data() {
        return {
            portfolio: {},
            pid: ""
        }
    },

    methods: {
        getInfo:function(){
            this.pid = this.$route.params.pid
        }
    },
    mounted(){
        this.getInfo();
        FirebaseService.getPortfolioById(this.pid)
        .then(res => { this.portfolio = res[0] })
    }

}

</script>

<style scoped>
div{
    margin-top: 70px;
}
</style>

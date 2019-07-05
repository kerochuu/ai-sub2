<template>
    <!-- show일 때만 버튼이 보이도록 설정 -->
    <div v-bind:class="{ active : show }" v-if="show">
        <!-- button을 클릭하면 위의 페이지로 이동 -->
        <button type="button" name="top" v-on:click="pageup">Top</button>
    </div>
</template>

<script>
export default {
    name: "Scroll",
    data() {
        return {
            show: false
        }
    },
    methods: {
        pageup: function() {
            window.scrollTo(0, 0);
        },
        CheckScroll: function() {
            if (window.scrollY === 0) {
                this.show = false
            } else {
                this.show = true
            }
        }
    },
    created: function() {
        window.addEventListener('scroll', this.CheckScroll)
    }
}
</script>

<style scoped>
button {
    position: fixed;
    right: 25px;
    font-family: 'Montserrat', sans-serif;
    color :#f0f0f0;
    font-weight: bolder;
    bottom: 70px;
    z-index: 1;
    font-size: 20px;
    border: solid 2px rgba(74,115,55, 0.8);
    background-color:	rgba(107,140,33, 0.8);
    border-radius: 10px;
    padding: 10px 20px;
}

</style>

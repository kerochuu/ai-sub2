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
    bottom: 30px;
    z-index: 1;
    font-size: 20px;
    font-weight: bold;
    border: solid 1px #333;
    background-color: #faacf1;
    border-radius: 10px;
    padding: 10px 20px;
}

</style>

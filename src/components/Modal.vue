<template>
  <div class="modal-mask">
    <div class="modal-wrapper">
      <div class="modal-container">

        <div class="modal-header">
          <slot name="header">
            <h1>Login</h1>
          </slot>
        </div>

        <div class="modal-body">
          <slot name="body">
            <h4>이메일</h4>
            <input type="email"></input>
            <h4>비밀번호</h4>
            <input type="password"></input>
            <div>
              <button>Login</button>
            </div>
          </slot>
        </div>

        <v-flex xs12 text-xs-center>
          <v-btn round color="#df4a31" dark v-on:click="loginWithGoogle" style="width:100%;"><v-icon size="25" class="mr-2">fa-google</v-icon> Google 로그인</v-btn>
          <v-btn round color="#3b5998" dark v-on:click="loginWithFacebook" style="width:100%;"><v-icon size="25" class="mr-2">fa-facebook</v-icon> Facebook 로그인</v-btn>
        </v-flex>

        <div class="modal-footer">
          <slot name="footer">
            <button class="modal-default-button" @click="close">
            Cancel
            </button>
            <button class="modal-default-button" @click="close">
              <router-link to="/signup">Sign Up</router-link>
            </button>
          </slot>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import FirebaseService from '@/services/FirebaseService'


export default {
    name: "Modal",
    data() {
        return {
            showsignup: false,
        }
    },
    methods: {
        close: function(){
            this.$emit('update');
        },
		async loginWithGoogle() {
			const result = await FirebaseService.loginWithGoogle()
			this.$store.state.accessToken = result.credential.accessToken;
			this.$store.state.user = result.user;
            console.log(this.$store.state.accessToken);
            console.log(this.$store.state.user);
            },
        async loginWithFacebook() {
            const result = await FirebaseService.loginWithFacebook()
            this.$store.state.accessToken = result.credential.accessToken;
            this.$store.state.user = result.user;
            console.log(this.$store.state.accessToken);
            console.log(this.$store.state.user);
		}
	},
}
</script>


<style scoped>

.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);
  display: table;
  transition: opacity .3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 300px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
  transition: all .3s ease;
  font-family: Helvetica, Arial, sans-serif;
}

.modal-header h1 {
  text-align: center;
}

.modal-body {
  margin: 20px 0;
}

.modal-body > input {
    width: 100%;
}

.modal-default-button {
  float: right;
  padding-left: 10px;
}

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}

input {
    border: solid 1px #333;
    border-radius: 5px;
}

</style>
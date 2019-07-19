<template>
  <div>
    <v-container>
            <div>
        <h1 style="text-align:center; font-size:8vh; margin-top:100px">Signup Page</h1>
      </div>
      <v-layout style="margin-top: 30%">
        <h4>이메일</h4>
        <input v-model="email" type="email" />
        </v-layout><v-layout style="margin-top: 20px">
        <h4>비밀번호</h4>
        <input v-model="password" type="password" />
        </v-layout><v-layout style="margin-top: 20px">
          <button @click="signup">Sign Up</button>
        </v-layout>
    </v-container>
  </div>
</template>

<script>
import FirebaseService from "@/services/FirebaseService";
import ImgBanner from "../components/ImgBanner";

export default {
  name: "SignUpPage",
  data() {
    return {
      email: "",
      password: ""
    };
  },
  components: {
    ImgBanner
  },
  methods: {
    signup: function() {
      FirebaseService.signupInFirebase(this.email, this.password);
    },
    async loginWithGoogle() {
      const result = await FirebaseService.loginWithGoogle();
      this.$store.state.accessToken = result.credential.accessToken;
      this.$store.state.user = result.user;
      console.log(this.$store.state.accessToken);
      console.log(this.$store.state.user);
    },
    async loginWithFacebook() {
      const result = await FirebaseService.loginWithFacebook();
      this.$store.state.accessToken = result.credential.accessToken;
      this.$store.state.user = result.user;
      console.log(this.$store.state.accessToken);
      console.log(this.$store.state.user);
    }
  },
  mounted() {
    console.log(this.$store.state);
  }
};
</script>

<style scoped>
input {
  border: solid 1px #333;
  border-radius: 5px;
}
</style>

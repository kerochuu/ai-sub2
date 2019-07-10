<template>
  <div>
    <v-toolbar fixed>
      <v-toolbar-title id="title">
        <router-link to="/" class="logo-text" style="text-decoration:none; color:#333">
          <v-icon size="25" class="mr-2">fa-home</v-icon>Home
        </router-link>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn v-for="item in menu" :key="item.url" class="link-button" flat>
          <router-link class="link-text" :to="'/'+item.url">{{ item.title }}</router-link>
        </v-btn>
        <!-- Login Icon 분할 -->
        <v-btn class="link-button" v-if="!user" flat>
          <p class="link-text" v-on:click="showLogin">login</p>
        </v-btn>
        <v-btn class="link-button" v-if="user" flat>
          <p class="link-text" v-on:click="logout">logout</p>
        </v-btn>
      </v-toolbar-items>
      <v-menu class="hidden-md-and-up">
        <v-toolbar-side-icon slot="activator">
          <v-icon>apps</v-icon>
        </v-toolbar-side-icon>
        <v-list class="hbmenu">
          <v-list-tile v-for="item in menu" :key="item.url">
            <v-list-tile-content>
              <router-link class="link-text" :to="'/'+item.url">
                <v-icon id="icon" size="25" class="mr-2">fa-{{ item.icon }}</v-icon>
                {{ item.title }}
              </router-link>
            </v-list-tile-content>
          </v-list-tile>
          <!-- Login Icon 분할 -->
          <v-list-tile-content v-if="!user">
            <p class="link-text" v-on:click="showLogin">
              <v-icon id="icon" size="25" class="mr-2">fa-unlock</v-icon>login
            </p>
          </v-list-tile-content>
          <v-list-tile-content v-if="user">
            <p class="link-text" v-on:click="logout">
              <v-icon id="icon" size="25" class="mr-2">fa-lock</v-icon>logout
            </p>
          </v-list-tile-content>
        </v-list>
      </v-menu>
    </v-toolbar>
    <Modal v-if="showmodal" v-on:update="showLogin"></Modal>
  </div>
</template>

<script>
import Modal from "./Modal";
import FirebaseService from "../services/FirebaseService";

export default {
  name: "Header",
  components: {
    Modal
  },
  data() {
    return {
      showmodal: false,
      menu: [
        {
          url: "post",
          title: "post",
          icon: "envelope"
        },
        {
          url: "portfolio",
          title: "portfolio",
          icon: "folder-open"
        },
        {
          url: "PortfolioWrite",
          title: "PortfolioWrite",
          icon: "pencil"
        }
      ]
    };
  },
  methods: {
    showLogin: function() {
      this.showmodal = !this.showmodal;
    },
    logout: function() {
      FirebaseService.signout();
      this.$router.push("/pass");
    }
  },
  props: {
    user: { type: Object }
  }
};
</script>

<style scoped>
.theme--light.v-toolbar {
  background-color: rgb(182, 133, 90);
}

.link-text {
  text-decoration: none;
  font-family: "Montserrat", sans-serif;
  font-weight: bolder;
  font-size: 20px;
  color: #604f3e;
}
.hbmenu {
  font-weight: bold;
}
#title {
  font-family: "Montserrat", sans-serif;
  font-weight: bold;
  font-size: 23px;
  color: #604f3e;
}
#icon {
  color: #604f3e;
}
</style>

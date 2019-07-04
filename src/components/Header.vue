<template>
  <v-toolbar fixed>
    <v-toolbar-title id="title">
      <router-link to="/" class="logo-text" style="text-decoration:none; color:#333">
        <v-icon size="25" class="mr-2">fa-home</v-icon>
      Home
      </router-link>
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-toolbar-items class="hidden-sm-and-down">
      <v-btn v-for="item in menu" :key="item.url" class="link-button" flat>
        <router-link class="link-text" :to="'/'+item.url">{{ item.title }}</router-link>
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
              <font-awesome-icon icon="spinner"></font-awesome-icon>
              <v-icon size="25" class="mr-2">fa-{{ item.icon }}</v-icon>
              {{ item.title }}
            </router-link>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-menu>
  </v-toolbar>
</template>

<script>

export default {
  name: "Header",
  data() {
    return {
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
          url: "login",
          title: "login",
          icon: "unlock"
        },
        {
          url: "PortfolioWrite",
          title: "PortfolioWrite",
          icon: "pencil"
        }
      ]
    };
  },
  methods: {}
};
</script>

<style scoped>
.v-toolbar__content {
  min-height: 60px !important;
  max-height: 60px !important;
}
.link-text {
  text-decoration: none;
  color: #333;
}
.hbmenu{
  font-weight: bold;
}

</style>

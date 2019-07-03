<template>
  <v-toolbar fixed>
    <v-toolbar-title>
      <router-link to="/" class="logo-text" style="text-decoration:none; color:#333">
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
          url: "",
          title: "home",
          icon: "home"
        },
        {
          url: "post",
          title: "post",
          icon: "email"
        },
        {
          url: "portfolio",
          title: "portfolio",
          icon: "home"
        },
        {
          url: "login",
          title: "login",
          icon: "home"
        },
        {
          url: "PortfolioWrite",
          title: "PortfolioWrite",
          icon: "home"
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

/* .header {
  background-color: #f0f0f0;
  height: 70px;
  font-family: 'Gaegu', cursive;
  font-size: 20px;
  font-weight: 700;
  padding: 25px;
  box-sizing: border-box;
  border: none;
  position: fixed;
  z-index: 100;
  width: 100%;
  overflow: hidden;
}
.header .icon{
  display: none;
}
.home{
  display: inline-block;

}
.menu-icon{
  display: inline-block;
  float: right;
}

button{
  padding-left: 20px;
}

a{
  text-decoration: none;
  color: #333;
  letter-spacing: 3px;
}

a:hover {
  padding: 10px;
  background-color: #555;
  color: white;
}

#md-icons {
  display: block;
}

#hamburger {
  display: none;
}

#menuIcon > button {
  display: none;
}

@media screen and (max-width: 720px){
  #hamburger {
    display: block;
  }
  .menu-icon a:not(:first-child) {
    display: none;
  }
  .menu-icon a.icon{
    float: right;
    display: block;
  }

  #md-icons {
    display: block;
  }

  #menuIcon > button {
    display: block;
  }
}

@media screen and (max-width: 720px) {
  .responsive .icon{
    position: absolute;
    right: 0;
    top: 0;
  }
  .menu-icon.responsive a{
    float: none;
    display: block;
    text-align: left;
  }
} */
</style>

<template>
  <footer>
    <strong>zooo1's</strong>
    <div id="snsIcon">
      <strong class="mr-3">contact</strong>
      <a href="https://github.com/zooo1"><v-icon size="30" class="mr-3">fa-github</v-icon></a>
      <router-link to="#"><v-icon size="30">fa-facebook-square</v-icon></router-link>
    </div>
  
  </footer>
</template>

<script>
export default{
  name: "Footer"
}
</script>

<style scoped>
footer{
  background-color: rgb(182, 133, 90);
  height: 50px;
  font-family: 'Montserrat', sans-serif;
  font-size: 20px;
  font-weight: 700;
  padding: 15px;

}
a {
  text-decoration: none;
}
strong{
  margin: 0 3;
}
#snsIcon{
  color: #333;
  float: right;
}

</style>

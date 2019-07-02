<template>
  <div class="header">
    <router-link to="/"><span>Blog</span></router-link>

      <div class="menu-icon">
        <button type="button" name="button">
          <router-link to="/post">POST</router-link>
        </button>
        <button type="button" name="button">
          <router-link to="/portfolio">Portfolio</router-link>
        </button>
        <button type="button" name="button">
          <router-link to="/Login">Login</router-link>
        </button>
      </div>

  </div>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style scoped>

.header {
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

</style>

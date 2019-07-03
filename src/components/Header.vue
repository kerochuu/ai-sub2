<template>
  <div class="header">
    
    <div class="home">
      <router-link to="/">Home</router-link>
    </div>
    
      <div class="menu-icon" id="menuIcon">
        <div id="md-icons">
          <button type="button" name="button">
            <router-link to="/post">POST</router-link>
          </button>
          <button type="button" name="button">
            <router-link to="/portfolio">Portfolio</router-link>
          </button>
          <button type="button" name="button">
            <router-link to="/Login">Login</router-link>
          </button>

          <button type="button" name="button">
            <router-link to="/PortfolioWrite">포트폴리오 작성</router-link>
          </button>

        </div>
        

        <button type="button" name="button">
          <router-link to="javascript:void(0);" onclick="myFunction()"><i class="fa fa-bars"></i></router-link>
        </button>
      </div>

  </div>
</template>

<script>
export default {
  name: "Header"
}

function myFunction(){
  var x = document.getElementById("menuIcon");
  if(x.className ==="menu-icon"){
    x.className += "reponsive";
  }
  else{
    x.className = "header";
  }
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

#menuIcon > button {
  display: none;
}

@media screen and (max-width: 720px){
  .menu-icon a:not(:first-child) {
    display: none;
  }
  .menu-icon a.icon{
    float: right;
    display: block;
  }

  #md-icons {
    display: none;
  }

  #menuIcon > button {
    display: block;
  }
}

@media screen and (max-width: 720px) {
  .menu-icon.responsive {position: relative;}
  .menu-icon.responsive .icon{
    position: absolute;
    right: 0;
    top: 0;
  }
  .menu-icon.responsive a{
    float: none;
    display: block;
    text-align: left;
  }
}
</style>

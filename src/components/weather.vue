<template>
  <div id="weather" width="30%">
    <list>
      <ul>
        <img :src="img_url"></img>
      </ul>
      <ul>
      </ul>
      <ul>
        <li>습도 : {{humidity}}%</li>
        <li>현재온도 : {{temp}}</li>
        <li>최고온도 : {{temp_max}}</li>
        <li>최저온도 : {{temp_min}}</li>
      </ul>
    </list>
  </div>
</template>

<script>
//날씨 api 추가. using openweathermap API
var weatherApiId="eff5a88bc9e0ad23fa3b728424ed8adb";
var city="Seoul"
var apiURI = "http://api.openweathermap.org/data/2.5/weather?q="+city+"&appid="+weatherApiId;

export default{
  name: "weather",
  data (){
    return{
      city : "",
      weather : "",
      humidity : "",
      pressure : "",
      temp : 0,
      temp_max : 0,
      temp_min : 0,
      img_url : "",
    }
  },
  created(){
    fetch(apiURI)
    .then((response) => {
      if(response.ok){
        return response.json();
      }
      throw new Error("Network response was not ok");
    })
    .then((json) => {
      //console.log(json);
      this.city = json.name;
      this.weather = json.weather[0].main;
      this.humidity = json.main.humidity;
      this.pressure = json.main.pressure;
      this.temp = (json.main.temp - 273.15).toFixed(1) + "°C";
      this.temp_max = (json.main.temp_max - 273.15).toFixed(1) + "°C";
      this.temp_min = (json.main.temp_min - 273.15).toFixed(1) + "°C";
      this.img_url = "http://openweathermap.org/img/w/" + json.weather[0].icon + ".png";
    })
    .catch((error) => {
      console.log(error);
    })
  }
}
</script>
<style>
#weather{
  font-size: 9pt;
  z-index: 4;
  background-color: rgb(182, 133, 90);
}
li{
  list-style: none;
}
ul{
  float:left;
}
</style>

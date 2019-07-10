<template>
  <div id="weather" width="30%">
    <v-list dense>지역 : {{city}}</v-list>
    <v-list dense>날씨 : {{weather}}</v-list>
    <v-list dense>습도 : {{humidity}}%</v-list>
    <v-list dense>현재온도 : {{temp}}</v-list>
    <v-list dense>최고온도 : {{temp_max}}</v-list>
    <v-list dense>최저온도 : {{temp_min}}</v-list>
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
      this.temp = (json.main.temp - 273.15).toFixed(2);
      this.temp_max = (json.main.temp_max - 273.15).toFixed(2);
      this.temp_min = (json.main.temp_min - 273.15).toFixed(2);
    })
    .catch((error) => {
      console.log(error);
    })
  }
}
</script>
<style>
#weather{
  font-size: 10pt;
}
</style>

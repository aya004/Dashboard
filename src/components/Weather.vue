<template>

  <div class="weather">
    <h2>Today's Weather</h2>
    <div class="card"><div class="design">
      <img :src = icon>
      <div class="details">
        <h3>{{city}}</h3>
        <div class="temp">
          {{temp}}
        </div>
        <div class="minmax">
          {{tempMax}}/{{tempMin}}
        </div>
        <div class="desc">
          {{description}}
        </div>
      </div></div>
      <div class="airQuality">
        <h3>COMFORT LEVEL</h3>
        <div class="feelsLike">
          Feels like:{{feelsLike}}
        </div>
        <div class="humidity">
          Humidity:{{humidity}}
        </div>
      </div>
      <div class="footer">
        <h3>SUNRISE/SUNSET</h3>
        <div class="sunrise">
          Sunrise: {{sunrise}}
        </div>
        <div class="sunset">
          Sunset: {{sunset}}
        </div>
      </div>
   </div>
  </div>

</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios,axios)
export default {
  data(){
    return{
      city: "",
      temp:"",
      tempMax:"",
      tempMin:"",
      description:"",
      humidity:"",
      feelsLike:"",
      windSpeed: "",
      sunrise: "",
      sunset: "",
      icon:"",
    }
  },
  mounted(){
    Vue.axios.get('https://api.openweathermap.org/data/2.5/weather?q=Berlin&units=metric&appid=a878e62677056ab40652dee58afd37c2')
    .then(response =>{
      console.log(response)
      this.city = response.data.name;
      this.temp = Math.round(response.data.main.temp);
      this.tempMax = Math.round(response.data.main.temp_max);
      this.tempMin = Math.round(response.data.main.temp_min);
      this.humidity = Math.round(response.data.main.humidity) + '%';
      this.feelsLike = Math.round(response.data.main.feels_like);
      this.windSpeed = Math.round(response.data.wind.speed) + 'm/s';
      this.sunrise = new Date(response.data.sys.sunrise*1000).toLocaleTimeString("en-GB");
      this.sunset = new Date(response.data.sys.sunset*1000).toLocaleTimeString("en-GB");
      this.icon = "http://openweathermap.org/img/wn/" + response.data.weather[0].icon + "@2x.png";
      this.description = response.data.weather[0].description;

    })
  }
}
</script>

<style scoped>
.weather{
  border: 1px hidden black;
     background-color:rgb(205, 190, 195);
     margin-top: 20px;
     border-radius: 12px;
}

.weather h2{
  text-align: center;
     margin-top: 0;
     padding-bottom: 10px;
     padding-top: 0;
     margin-bottom: 0;
}
.card{
     padding-top: 10px;
	padding-bottom: 10px;
	padding-left: 10px;
	padding-right: 10px;
 }
 .card img{
   float: left;
	display: grid;
	padding-top: 10px;
	padding-bottom: 10px;
	padding-right: 12px;
 }
 .details{
   display: flex;
	flex-direction: column;
	flex-wrap: wrap;
  text-align: center;
  
 }
 .design{
   border-bottom: 1px solid white;
   padding-bottom: 10px;
 }
 .airQuality{
   border-bottom: 1px solid white;
   padding-bottom: 10px;
   padding-top: 10px;
 }
 .airQuality h3{
   margin: 0;
   padding-bottom: 12px;
 }
 .feelsLike{
   float: left;
	display: grid;
  padding-right: 12px;
 }
 .humidity{
   display: flex;
	flex-direction: column;
	flex-wrap: wrap;
 }
 .footer{
   padding-bottom: 10px;
   padding-top: 10px;
 }
 .footer h3{
   margin: 0;
   padding-bottom: 12px;
 }
</style>
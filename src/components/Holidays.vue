<template>
    <div class="holiday">
       <h2> Next holiday </h2>
       <div>
           <div class="card">
              <h3> {{nextHoliday.name}} </h3>
              <div class="date">{{nextHoliday.date.iso}}</div>
              <div class="desc">{{nextHoliday.description}}</div>
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
            nextHoliday: []

        }
    },
    mounted(){
        const url = "https://calendarific.com/api/v2/holidays?&api_key=a56c3f85deb30a2fd7903d8a3b88a219744b6f1d&country=de&year=2022&location=de-be";
        Vue.axios.get(url).then(resp =>{
            console.log(resp);
            this.nextHoliday = resp.data.response.holidays[10];
            console.log(this.nextHoliday)
            
            
        })
    }
}
</script>

<style scoped>
.holiday{
    border: 1px hidden;
     background-color:rgb(205, 190, 195);
     border-radius: 12px;
     margin-top: 20px;
  
}
.holiday h2{
    text-align: center;
     margin-top: 0;
     padding-bottom: 10px;
     padding-top: 0;
     margin-bottom: 0;
}
.name{
    padding-bottom: 10px;
}
.date{
    padding-bottom: 10px;
    color: cadetblue;
}
.desc{
    padding-bottom: 20px;
}
.card{
     padding-top: 10px;
	padding-bottom: 10px;
	padding-left: 10px;
	padding-right: 10px;
}
</style>
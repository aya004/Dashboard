<template>
<div class="bvg">
    <h2>
        S+U Tempelhof
    </h2>
    <div class="card">
        <div class="lineName">{{fLineName}}</div>
        <div class="details">
        <div class="richtung">{{fDirection}}</div>
        
        <div class="time">{{fTime}}</div>
        <div class="delay">{{fDelay}}</div>
        </div>
    </div>
    <div class="card">
        <div class="lineName">{{sLineName}}</div>
        <div class="details">
        <div class="richtung">{{sDirection}}</div>
        
        <div class="time">{{sTime}}</div>
        <div class="delay"> {{sDelay}}</div>
        </div>
    </div>
    
    
</div>

</template>
<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios,axios)


export default{
    
    data(){
        return{
            
                stopName:"",
                fLineName:"",
                fDirection:"",
                fTime:"",
                fDelay:"",
                sLineName: "",
                sDirection: "",
                sTime: "",
                sDelay: ""
                
            
        }

    },

    
    mounted(){
        const url ='https://v5.vbb.transport.rest/stops/900068201/departures?&linesOfStops=true&remarks=true&language=en';
        axios.get(url).then(response => {
            console.log(response);
            
            this.fLineName= response.data[0].line.name;
            this.fDirection= response.data[0].direction;
            this.fTime = new Date(response.data[0].when).toLocaleTimeString('en',{timeStyle:'short', hour12:true});
            
            if (response.data[0].delay == "0") {

                console.log(response.data[0].delay)
                
            }
            else{

                this.fDelay = 'Delay: ' + response.data[0].delay + ' min';
            }
            

            this.sLineName= response.data[1].line.name;
            this.sDirection= response.data[1].direction;
            this.sTime = new Date(response.data[1].when).toLocaleTimeString('en',{timeStyle:'short', hour12:true});
            
            if (response.data[1].delay == "0") {

                console.log(response.data[1].delay)
                
            }
            
            else{

                this.sDelay = 'Delay: '+ response.data[1].delay + ' min';
            }

            
            
        })
    }
}

</script>
<style scoped>
.bvg{
   border: 1px hidden;
      background-color:rgb(205, 190, 195);
     border-radius: 12px;
     margin-top: 20px;
}
.bvg h2{
    text-align: center;
    margin-top: 0;
    padding-bottom: 10px;
    padding-top: 0;
    margin-bottom: 0;;
}
.first{
    padding-bottom: 20px;
}
.lineName{
    display: grid;
    float: left;
    padding-top: 10px;
	padding-bottom: 10px;
	padding-right: 20px;
}
.details{
    display: flex;
	flex-direction: column;
	flex-wrap: wrap;
}
.card{
      padding-top: 10px;
	padding-bottom: 10px;
	padding-left: 10px;
	padding-right: 10px;
}
.delay{
    color: crimson;
}

</style>
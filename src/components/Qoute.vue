<template>
    
    <div class="qoute">
        <h2>Qoute of the day:</h2>
        <div class="card">
            <div class="text">{{en}}</div>
            <div class="author"><h3>{{author}}</h3></div>
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
            en: "",
            author: ""
            
        }
    },
    mounted(){
        
            const url = "https://programming-quotes-api.herokuapp.com/Quotes?count=0";
           Vue.axios.get(url)
            .then(response => {
            console.log(response)
            this.en = response.data[0].en;
            this.author = response.data[0].author;
            
            

            });
        
    },

}
</script>

<style scoped>
.qoute{
     border: 1px hidden;
      background-color:rgb(205, 190, 195);
     border-radius: 12px;
     margin-top: 20px;
     
}
.card{
     padding-top: 10px;
	padding-bottom: 10px;
	padding-left: 10px;
	padding-right: 10px;
}
.qoute h2{
 text-align: center;
     margin-top: 0;
     padding-bottom: 10px;
     padding-top: 0;
     margin-bottom: 0;
}
.author h3{
    color: cadetblue;
}
</style>
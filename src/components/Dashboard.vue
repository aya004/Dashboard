<template><div class="dashboard">
    <header>
        <h1>Dashboard</h1>
    </header>
    <div class="grid-container">
        <div class="item1">
            <weather/>
        </div>
        <div class="item2">
            <qoute/>
        </div>
        <div class="item3">
            <bvg/>
        </div>
        <div class="item4">
            <holidays/>
        </div>
        <div class="item5">
            <twitter/>
        </div>
        <div class="footer">
            <wikipedia/>
        </div>

        
    </div></div>
</template>


<script>
import Bvg from './Bvg.vue'
import Holidays from './Holidays.vue'
import Qoute from './Qoute.vue'
import Twitter from './Twitter.vue'
import Weather from './Weather.vue'
import Wikipedia from './Wikipedia.vue'

export default {
    name:"dashboard",
    components:{
        Weather,
        Bvg,
        Qoute,
        Holidays,
        Twitter,
        Wikipedia
        
       
    }
    
}
</script>

<style>
.dashboard h1{
    text-align: center;
    color: rgb(167, 167, 167);
    border-bottom: 1px solid rgb(167, 167, 167);
    padding-bottom: 20px;
    padding-top: 20px;
    margin: 0;
    box-shadow: 0 8px 20px -1px  rgb(167, 167, 167) ;
}

.grid-container{
    padding-top: 10px;
}
@media screen and (min-width: 720px){
    .grid-container{
        display: grid;
        grid-template-columns: 1.3fr 1fr 1.5fr;
        grid-gap: 10px
    }
    .item1{
        grid-row-start: 1;
        grid-row-end: 3;
        background-color: rgb(205, 190, 195) ;
        border-radius: 12px;
        
    }
    .item2{
        grid-row-start: 1;
        grid-row-end: 2;
        background-color: rgb(205, 190, 195) ;
        border-radius: 12px;
        
    }
    .item3{
        grid-row-start: 1;
        grid-row-end: 2;
        background-color: rgb(205, 190, 195) ;
        border-radius: 12px;
        
    }
    .item4{
        grid-row-start: 2;
        grid-row-end: 3;
        background-color: rgb(205, 190, 195) ;
        border-radius: 12px;
       
    }
    .item5{
        grid-row-start: 2;
        grid-row-end: 3;
        background-color: rgb(205, 190, 195) ;
        border-radius: 12px;
       
    }
    .footer{
        grid-row-start: 3;
        grid-column-start: 1;
        grid-column-end: 4;
        background-color: rgb(205, 190, 195) ;
        border-radius: 12px;
    }
}

</style>
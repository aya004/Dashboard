<template>
    <div class="twitter">
        
            <h2>Recents on Twitter</h2>
        
        <div class="card">
            <img src="../assets/giraffe.jpg" height="64px" width="64px">
            <div class="tweet">
                <h3>BoxOfPoptarts</h3>
                <p>Every single time masks come off, another<span class="hashtag"> #COVID </span> sweeps the country. I’ll be leaving my mask on. Lesson learned.</p>
            </div>
        </div>
        
    </div>
</template>

<script>
export default{

}
</script>

<style scoped>
 .twitter{
    border: 1px hidden;
     background-color:rgb(205, 190, 195);
     border-radius: 12px;
     margin-top: 20px;
     
 }
 .twitter h2{
     text-align: center;
     margin-top: 0;
     padding-bottom: 10px;
     padding-top: 0;
     margin-bottom: 0;

 }
 .hashtag{
  color: cornflowerblue;
  
 }
 .card{
     padding-top: 10px;
	padding-bottom: 10px;
	padding-left: 10px;
	padding-right: 10px;
 }
 .card img{
    border-radius: 70%;
	float: left;
	display: grid;
	padding-top: 10px;
	padding-bottom: 10px;
	padding-right: 12px;
 }
 .tweet {
    display: flex;
	flex-direction: column;
	flex-wrap: wrap;
 }
 .tweet h2{
     margin-top: 10px;
     margin-bottom: 10px;
 }
 .tweet p{
     margin-top: 0 ;
     
 }
 .card h3{
     padding-top: 10px;
     padding-bottom: 10px;
     margin: 0;
 }
 
</style>
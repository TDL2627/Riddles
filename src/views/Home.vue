<template>
  <div class="home">
 
 <h1 class="mainHead">RIDDLE GAME</h1>

 <div id="nav">
    
        <router-link to="/quiz"><h2 class="go">LETS GO</h2></router-link> 

  </div>
  </div>
</template>

<script>


export default {


}
</script>
<style scoped>
.home{
  padding-top: 15%;
}
.mainHead{
  color: whitesmoke;
  font-size: 100px;
}
.go{
  border: 2px solid rgb(253, 81, 1);
  background: white;
  color:  rgb(253, 81, 1);
  border-radius:25px ;
  padding: 20px;
}
</style>

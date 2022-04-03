<template>
  <div class="home">
 <div class="headline">
 <h1 class="mainHead animate__animated  animate__bounceInDown">RIDDLE GAME</h1>
 </div>

 <div id="nav">
        <router-link to="/quiz"><h2  class="go animate__animated  animate__jackInTheBox animate__delay-2s ">LETS GO</h2></router-link> 
  </div>
  <h1 class="creator animate__animated animate__hinge animate__delay-3s animate__slower">TDL2627</h1>
  </div>
</template>

<script>


export default {


}
</script>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@500&family=Rubik+Glitch&display=swap');
.home{
  padding-top: 15%;
}
.mainHead{
  color: whitesmoke;
  font-size: 100px;
}
.creator{
  color: red;
  font-size: 70px;
  margin-top:5%;
font-family: 'Rubik Glitch', cursive;
}

.headline{
  animation-name: vibrate-1;
  animation-duration: 1s;
  animation-iteration-count: infinite;
}
.go{
  border: 2px solid rgb(253, 81, 1);
  background: white;
  color:  rgb(253, 81, 1);
  border-radius:25px ;
  margin-left: 25%;
  margin-top: 5%;
  padding: 20px;
  overflow: hidden !important;
  width: 50%;
}
.go:hover{
 border: 2px solid white ;
  background: rgb(253, 81, 1);
  color:  white;
}
@media only screen and (max-width:700px) {
  .home{
      padding-top: 50%;
  }
  .mainHead{
    font-size: 40px;
  }
.go{
  margin-top: 40%;
}
.creator{
      font-size: 40px;

}
}
</style>

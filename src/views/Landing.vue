<template>
  <div class="landing">
    <div class="background-video">
      <Typed />
      <video playsinline autoplay muted loop poster="polina.jpg" id="bgvid">
        <source src="../assets/video/tour-opt.mp4" type="video/mp4">
      </video> 
    </div>
  </div>
</template>
<script>
import Typed from '../components/Typed'
export default {
components:{Typed}
}
</script>
<style>
 .background-video  {
    color:white;
    display:flex;
    align-items: center;
    justify-content: center;
    background-color:rgba(56, 56, 56, 0.418);
    height:100vh;
    width:100vw;
    object-fit: cover;
    top:0;
    left:0;
    z-index:1;
 }
/* ----------- iPhone X ----------- */

/* Portrait and Landscape */
@media only screen 
  and (min-device-width: 375px) 
  and (max-device-width: 812px) 
  and (-webkit-min-device-pixel-ratio: 3) { 
  
  .landing{
    background:url("../assets/backgrounds/mobile-map.jpg") no-repeat center center fixed;
    -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  }
}
video{
  z-index: -1;
  object-fit: cover;
  width: 100vw;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
}
</style>
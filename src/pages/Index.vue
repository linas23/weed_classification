<template>
  <q-page class="bg-green-10" >
    <div class="row hero">
      <div class="col-6 q-pa-xl text-white">
        <div class="text-h1">
          Weed Classification
        </div>
        <p class="text-h4 q-mt-xl">
          Select an image of the weed.
        </p>
        <div class="text-h5">
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Incidunt et cumque magnam velit architecto saepe sed ipsa 
        </div>
        <q-img id="weedPlant" src="/images/pngwing.com (2).png" height="100px" width="100px"></q-img>
      </div>
      <div class="col-6 self-end">
        <lottie-player src="https://assets7.lottiefiles.com/packages/lf20_rg8y5nzn.json"  background="transparent"  speed="1"  :style="animationStyle.desktop"  loop  autoplay></lottie-player>
      </div>
      <div class="addFileButton">
        <q-btn flat class="self-center">Select Image</q-btn>
      </div>
      <div id="smoke" type="flex" class="row">
        <!-- <lottie-player  src="https://assets10.lottiefiles.com/packages/lf20_sXcjxz.json"  background="transparent"  speed="1"  :style="animationStyle.mobile"  loop  autoplay></lottie-player> -->
      </div>
    </div>
  </q-page>
</template>

<script>
import "@lottiefiles/lottie-player";
export default {
  name: 'PageIndex',
  data(){
    return{
      animationStyle:{
        desktop:{
          width: "600px",height: "600px"
        },
        mobile:{
          width: "150px",height: "150px"
        },
        smoke:{
          width: "150px",height: "150px"
        }
      }
    }
  }
 
  }
</script>

<style lang="scss" scoped>
.hero{
  position:relative;
  height:90vh;
  .addFileButton{
    position: absolute;
    top:100%;
    left:50%;
    transform: translateX(-50%);
  }
 /*  #smoke{
    position:absolute;
    top:70%;
    left:50%;
    transform: translateX(-50%);
  }
     */
     #weedPlant{
       animation:turnAround 3s ease-in-out infinite alternate-reverse;
     }
     @keyframes turnAround {
       0%{
         transform: rotateY(0deg)
       }
       100%{

         transform: rotateY(180deg);
       }
     }
}
</style>

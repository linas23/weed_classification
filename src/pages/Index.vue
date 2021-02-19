<template>
  <q-page class="bg-green-9" >
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
        <!-- <q-img id="weedPlant" src="/images/pngwing.com (2).png" height="100px" width="100px"></q-img> -->
      </div>
      <div class="col-6  heroAnimationBox">
        <lottie-player id="animation" src="https://assets7.lottiefiles.com/packages/lf20_rg8y5nzn.json"  background="transparent"  speed="1"  :style="[animationStyle.desktop,lottieAnimation1]"  loop  autoplay></lottie-player>
      </div>
      <div class="addFileButton">
        <!-- <q-btn flat class="self-center">Select Image</q-btn> -->
        <q-img id="weedPlant" src="/images/pngwing.com (2).png" height="100px" width="100px"></q-img>

      </div>
     <!--  <div id="smoke" type="flex" class="row">

        <div v-for="i in 9" :key="i" class="col">
          <lottie-player  src="https://assets10.lottiefiles.com/packages/lf20_sXcjxz.json"  background="transparent"  speed="1"  :style="animationStyle.mobile"  loop  autoplay></lottie-player>
        </div>
      </div> -->
    </div>
    <div class="fileUpload flex flex-center column">
      <q-uploader
      label="Image Upload"
        :factory="factoryFn"
        style="max-width: 300px"
        @factory-failed="factoryFnFailed"
      />
      <q-banner rounded 
        style="max-width: 300px"
        v-if="errorMessage"  class="text-white text-center bg-blue q-mt-md">
      {{errorMessage}}
    </q-banner>
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
          width: "600px",height: "600px",
        },
        mobile:{
          width: "150px",height: "150px"
        },
        smoke:{
          width: "150px",height: "150px"
        }
      },
      animationPosition:{},
      errorMessage:""
    }
  },
  computed:{
    lottieAnimation1(){
      return this.animationPosition;
    }
  },
  mounted(){
    setInterval(()=>{
      let size = 1;
      let x = Math.floor(Math.random()*60) + 'px';
      let y = Math.floor(Math.random()*60) + 'px';
      this.animationPosition = {
        transform:`translate(${x},${y}) scale(${size})`,
        transition:'all .5s ease-in-out',
      }
      size=1;
    },222)
  },
  methods:{
    async factoryFn (files) {
      this.errorMessage=""
      let fd = new FormData();
        const image = files[0]
        console.log({image})
        fd.append('image',image)
        console.log({fd})
          let res = await this.$axios.post('http://localhost:4444/upload',{fd})
          console.log({res})
        
        // go to the detail page.

      /* return new Promise((resolve) => {
        // simulating a delay of 2 seconds
        setTimeout(() => {
          resolve({
            url: 'http://localhost:4444/upload'
          })
        }, 2000)
      }) */
    },
  factoryFnFailed(err){
    console.log({err})
    this.errorMessage=err.message      
    }
  }
}
</script>

<style lang="scss" scoped>
.hero{
  position:relative;
  height:100vh;
  .addFileButton{
    position: absolute;
    top:75%;
    left:50%;
    transform: translateX(-50%);
  }
  
    
     #weedPlant{
       animation:turnAround 1.5s ease-in-out infinite alternate-reverse;
     }
     @keyframes turnAround {
       0%{
         
         transform:scale(1.3) rotateY(0deg)
       }
       100%{

         transform: rotateY(180deg);
       }
     }
     /* .heroAnimationBox{
      // position:relative  !important;
      #animation{
        // position:absolute !important;
      } */
    
}
.fileUpload{
  height:100vh;
}
</style>

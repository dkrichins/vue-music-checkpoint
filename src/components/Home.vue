<template>
  <div class="home">
    <div class="background">
      <div class="container-fluid">
        <div class="row">
          <div class="col-xs-6">
            <div class="well">
              <itunes class="itunes"></itunes>       
            </div>
          </div>
          <div class="col-xs-6">
            <div class="well">
              <my-tunes class="my-tunes"></my-tunes>          
            </div>
          </div>
        </div>  
      </div>
    </div> 
  </div>
</template>

<script>

import MyTunes from './Mytunes'
import Itunes from './Itunes'

export default {
  name: 'home',
  data () {
    return {
      
    }
  },
  components: {
    MyTunes,
    Itunes
  }
}
</script>


<style>
/**
* YOU SHOULD PROBABLY MAKE THIS LOOK BETTER :)
* BOOTSTRAP IS FOR THE WEAK FLEXBOX IS KING
* -- McCall
**/
/*.my-tunes{  
  min-height: 500px;
  min-width: 50%;
  background: silver;
}

.itunes{  
  background: pink;
  min-height: 500px;
  min-width: 45%;
}
*/
.background{
  background: url("http://goldwallpapers.com/uploads/posts/music-studio-wallpaper/music_studio_wallpaper_024.jpg") no-repeat center center fixed;
  background-size: cover;
 
}

.well {
  opacity: .8;
  background: silver;
}

</style>

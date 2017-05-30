<template>
    <div class="my-tunes">
        <h1>MyTunes List:</h1>
        <div class="row" v-for="song in songs">
            <div class="col-xs-1 text-center">
                <img class="thumbnail" :src="song.artworkUrl60">
            </div>
            <div class ="col-xs-2">
                <h4>{{song.artistName}}</h4>
            </div>
            <div class = "col-xs-2">
                <h5>{{song.trackName}}</h5>
            </div>
            <div class = "col-xs-3">
                <audio controls><source :src='song.previewUrl'></audio>
            </div>
            <div class = "col-xs-1 col-xs-offset-1">
                <button type="button" @click="removeTrack(song)">Remove Track</button>                    
            </div>
            <div class = "col-xs-1">
                <button type="button" @click="promoteTrack(song)">Promote Track</button>                    
            </div>
            <div class = "col-xs-1">
                <button type="button" @click="demoteTrack(song)">Demote Track</button>                    
            </div>            
        </div>
    </div>
</template>
<script>

import myTunesService from '@/services/mytunes-service'

export default {
    name: 'my-tunes',
     data() {
        return {            
            // songs: []
            songs: myTunesService.getTracks()
        }
    },
    
    methods:{
        //getTracks(){
            // this.songs = myTunesService.getTracks()
           
       // },        
        removeTrack(song){
            myTunesService.removeTrack(song)
        }, 
        promoteTrack(song){
            myTunesService.promoteTrack(song)
            
        },
        demoteTrack(song){
            myTunesService.demoteTrack(song)
            
        }        
    },
    components:{}
}
</script>

<style scoped>

</style>
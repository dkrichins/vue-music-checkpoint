<template>
    <div class="itunes">
        <div class="container"> 
            <div class="row"> 
                <div class="col-xs-12">
                    <form class="form-inline" @submit.prevent="getMusic">
                    <div class="form-group">
                        <input type="text" class="form-control" v-model="artist" name="artist" placeholder="Artist Name" />
                        <button type="submit" class="btn btn-primary" id="get-music-button">Get Music</button>
                    </div>
                    </form>
                </div>  
            </div>
            <div class = "row" v-for='song in iTunes'>
                <div class ="col-xs-2">
                    <p>{{song.artistName}}</p>
                </div>
                <div class = "col-xs-2">
                    <p>{{song.trackName}}</p>
                </div>
                <div class = "col-xs-2">
                    <button type="button" @click="addTrack(song)">Add Track</button>
                </div>
            </div>
        </div>          
    </div>
</template>

<script>

import myTunesService from '@/services/mytunes-service'
import iTunesService from '@/services/itunes-service'

export default {
    name: 'itunes',
    data(){
        artist: ''
        iTunes: []
    },
    
    methods:{
        getMusic() {
            iTunesService.getMusicByArtist(this.artist).then(res=>{
                let resObj = JSON.parse(res)
                this.songs = resObj.results
            })
        },
        addTrack(song) {
            myTunesService.addTrack(song)
        }
 
    },
    components:{}
}
</script>


<style scoped>

</style>
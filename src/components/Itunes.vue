<template>
    <div class="itunes"> 
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
        <h1>Selected Itunes:</h1>
        <div class = "row" v-for='song in songs'>
            <div class="col-xs-1">
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
            <div class="col-xs-1 col-xs-offset-1">
                <h6>Price: {{song.collectionPrice}}</h6>
            </div>
            <div class = "col-xs-2">
                <button class="btn btn-primary" @click="addTrack(song)">Add To MyTunes</button>
            </div>
        </div>                  
    </div>
</template>

<script>

import myTunesService from '@/services/mytunes-service'
import iTunesService from '@/services/itunes-service'

export default {
    name: 'itunes',
     data() {
        return {
            artist: '',
            songs: []
        }
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
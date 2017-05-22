<template>
    <div class="my-tunes">
        <div class="container"> 
            <div class="row" v-for="song in myTunes">
                <div class ="col-xs-2">
                     <p>{{song.artistName}}</p>
                </div>
                <div class = "col-xs-2">
                    <p>{{song.trackName}}</p>
                </div>
                 <div class = "col-xs-1">
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
    </div>
</template>
<script>

import myTunesService from '@/services/mytunes-service'

export default {
    name: 'my-tunes',
    data(){
        myTunes: {}
    },
    
    methods:{
        getTracks(){
            this.myTunes = myTunesService.getTracks()
        },        
        removeTrack(song){
            this.myTunes = myTunesService.removeTrack(song)
        }, 
        promoteTrack(song){
             this.myTunes = myTunesService.promoteTrack(song)
        },
        demoteTrack(song){
             this.myTunes = myTunesService.demoteTrack(song)
        } 
    },
    components:{}
}
</script>

<style scoped>

</style>
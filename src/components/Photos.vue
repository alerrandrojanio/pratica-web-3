<template>
    <button @click="fetchPhotos">Fetch Photos</button>
    <ul>
        <li v-for="photo in photos" :key="photo.id">
            <h2>{{photo.title}}</h2>
            
            <img :src="photo.thumbnailUrl">
            <p>URL: {{photo.url}}</p>
        </li>
    </ul>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Photos',
        data() {
            return {
                photos: [],
                baseURI: "https://jsonplaceholder.typicode.com/photos"
        }; 
    },
    methods:{
        fetchPhotos: function(){
            axios.get(this.baseURI).then((result) => {
                this.photos = (result.data);
            });
        } 

    },
};
</script>

<style>

</style>
<template>
    <button @click="fetchAlbuns">Fetch Albuns</button>
    <ul>
        <li v-for="album in albuns" :key="album.id">
            <h2>{{album.title}}</h2>
            <img :src="album.url">
        </li>
    </ul>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Albuns',
        data() {
            return {
                albuns: [],
                baseURI: "https://jsonplaceholder.typicode.com/albums"
        }; 
    },
    methods:{
        fetchAlbuns: function(){
            axios.get(this.baseURI).then((result) => {
                this.albuns = (result.data);
            });
        } 

    },
};
</script>

<style>

</style>
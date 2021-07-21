<template>
    <button @click="fetchAlbuns">Fetch Albuns</button>
        <div  v-for="user in users" :key="user.id">
            <li>
                <h2>Nome: </h2>
                    <p>{{user.name}}</p>
                
                <div v-for="album in albuns" :key="album.id">
                    <div>
                        <ul>
                            <li v-if="album.userId === user.id">
                                <p>Título do album: {{album.title}}</p>

                                <h3>Fotos: </h3>
                                <ul>
                                    <div v-for="photo in photos" :key="photo.id">
                                        <li v-if="photo.albumId === album.id">
                                            <p>Título da foto: {{photo.title}}</p>
                                            <img :src="photo.thumbnailUrl">
                                            <p>URL: {{photo.url}}</p>
                                        </li>
                                    </div>
                                </ul>
                            </li>
                        </ul>
                    </div>
                </div>
            </li>
        </div>
</template>
<script>
import axios from 'axios';

export default {
    name: 'Albuns',
        data() {
            return {
                albuns: [],
                users: [],
                photos: []
                
        }; 
    },
    methods:{
         fetchAlbuns (){
            axios.all([
                axios.get('https://jsonplaceholder.typicode.com/albums'),
                axios.get('https://jsonplaceholder.typicode.com/users'),
                axios.get('https://jsonplaceholder.typicode.com/photos')
            ]).then(axios.spread((albunRes, userRes, photoRes)=>{
                this.albuns = albunRes.data
                this.users = userRes.data
                this.photos = photoRes.data
            }))
        }
    },
};
</script>

<style>

</style>
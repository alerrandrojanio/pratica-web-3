<template>
    <button @click="fetchPosts">Fetch Posts</button>
    <ul>
        <li v-for="post in posts" :key="post.id">
            <h2>{{post.title}}</h2>
             {{post.body}}
        </li>
    </ul>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Posts',
        data() {
            return {
                posts: [],
                baseURI: "https://jsonplaceholder.typicode.com/posts"
        }; 
    },
    methods:{
        fetchPosts: function(){
            axios.get(this.baseURI).then((result) => {
                this.posts = (result.data);
            });
        } 

    },
};
</script>

<style>

</style>
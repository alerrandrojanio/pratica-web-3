<template>
    <button @click="fetchPosts">Fetch Posts</button>
    <ul>
        <li v-for="(post, id) in posts" :key="id">
            <h2>{{post.title}}</h2>
             {{post.body}}
        </li>
        <li v-for="(user, id) in users" :key="id">
            <h2 v-if="user.id == 1">{{user.name}}</h2>
             
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
                users:[],
                comments:[]
        }; 
    },
    methods:{
        fetchPosts: function(){
            // axios.get(this.baseURI).then((result) => {
            //     this.posts = (result.data);
            // });

            axios.all([
                axios.get('https://jsonplaceholder.typicode.com/posts'),
                axios.get('https://jsonplaceholder.typicode.com/users'),
                axios.get('https://jsonplaceholder.typicode.com/comments')
            ]).then(axios.spread((postRes, userRes, commentsRes)=>{
                this.posts = postRes.data
                this.users = userRes.data
                this.comments = commentsRes.da
            }))
        }

    },
};
</script>

<style>

</style>
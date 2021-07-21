<template>
    <button @click="fetchPosts">Fetch Posts</button>
    <ul>
        <div v-for="user in users" :key="user.id">
            <li>
                <h2>Nome:</h2>
                    <p>{{user.name}}</p>

                <div v-for="post in posts" :key="post.id">
                    <div>
                        <ul>
                            <li v-if="post.userId === user.id">
                                <p>Title: {{post.title}}</p>
                                <p>Body: {{ post.body }}</p>
                                <h3>Comentários: </h3>
                                <ul>
                                    <div v-for="comment in comments" :key="comment.id">
                                        <li v-if="comment.postId === post.id">
                                            <p>Nome: {{comment.name}}</p>
                                            <p>Email: {{ comment.email }}</p>
                                            <p>Body: {{ comment.body }}</p>
                                        </li>
                                    </div>
                                </ul>
                            </li>
                        </ul>
                    </div>
                </div>
            </li>
        </div>
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
        fetchPosts (){
            axios.all([
                axios.get('https://jsonplaceholder.typicode.com/posts'),
                axios.get('https://jsonplaceholder.typicode.com/users'),
                axios.get('https://jsonplaceholder.typicode.com/comments')
            ]).then(axios.spread((postRes, userRes, commentsRes)=>{
                this.posts = postRes.data
                this.users = userRes.data
                this.comments = commentsRes.data
            }))
        }

    },
};
</script>

<style>

</style>
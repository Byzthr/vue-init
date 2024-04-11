<template>
    <div class="posts">
        <Post :key="post.id" v-for="post in posts" user="Viti" :post="post"/>
    </div>
</template>

<script>
import Post from './Post.vue';

export default {
    name: "Posts",
    props: {
        posts: Array,
    },
    components: {
        Post,
    }
}
</script>

<style>
.posts {
    max-width: 500px;
    display: grid;
    grid-template-columns: 33% 33% 33%;
    column-gap: .5%;
}
</style>

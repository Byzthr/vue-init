<template>
    <div class="post">
        <img :src="post.image" :alt="post.image">
        <p><a href="">{{ user }}</a>: {{ post.caption }}</p>
    </div>
</template>

<script>
export default {
    name: "Post",
    props: {
        user: String,
        post: Object,
    },
    methods: {

    }
}
</script>

<style>
.post {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

img {
    width: 100%;
}
</style>
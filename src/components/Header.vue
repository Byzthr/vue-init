<template>
    <header>
        <img
            alt="Profile picture"
            :src="require(`@/assets/${userData.userPPic}`)">
        <div class="userBio">
            <h1>{{ userData.userName }}</h1>
            <h2>{{ userData.userDesc }}</h2>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
        userData: Object,
        // userPPic: File,
    },
    created() {
        console.log(this.userData)
    }
}
</script>

<style scoped>
header {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 20px;
}
img {
    border-radius: 50%;
    max-width: 100px;
}
.userBio{
    margin: 0 2rem;
}
</style>
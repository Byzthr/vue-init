<template>
    <header>
        <img
            alt="Profile picture"
            :src="require(`@/assets/${userPPic}`)">
            <!-- :src="require(`@/assets/${userData.userPPic}`)"> -->
        <div class="userBio">
            <h1>{{ userData.user_name }}, {{ userData.age }}</h1>
            <h2>{{ userData.gym }}</h2>
            <h2>{{ userData.style }}</h2>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
        userData: Object,
        // userPPic: File,
        userPPic: String,
    },
    computed: {
        userAge() {
            var birdthDate = new Date(this.userData.birdth_date)
            var currentDate = new Date()
            var age = currentDate.getFullYear() - birdthDate.getFullYear()
            if (currentDate.getMonth() < birdthDate.getMonth() ||
                currentDate.getMonth() === birdthDate.getMonth() &&
                currentDate.getDay() < birdthDate.getDay()) age--
            return age
        } 
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
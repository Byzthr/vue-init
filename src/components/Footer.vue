<template>
    <div class="options-footer">
        <div @click="toProfile" class="footer-button" id="profile"><i class="fa-solid fa-user"></i></div>
        <div @click="toNotifications" class="footer-button" id="notifications"><i class="fa-solid fa-bell"></i></div>
        <div @click="toNewPost" class="footer-button" id="post"><i class="fa-solid fa-plus"></i></div>
    </div>
</template>

<script>
export default {
    name: "Footer",
    methods: {
        toProfile() {
            this.$emit("toProfile")
        },
        toNotifications() {
            this.$emit("toNotifications")
        },
        toNewPost() {
            this.$emit("toNewPost")
        }
    }
}
</script>

<style>
.options-footer {
    font-size: 2rem;
    width: 100%;
    background: lightgrey;
    display: flex;
    justify-content: space-around;
    position: fixed;
    bottom: 0;
}

.footer-button {
    width: 100%;
    padding: 1rem;
    cursor: pointer;
}
</style>

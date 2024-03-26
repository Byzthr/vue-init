<template>
    <button @click="onClick()" class="btn" :style="{ background: color }"><i class="fa-solid fa-user-plus"></i> Add</button>
</template>

<script>
    export default {
        name: 'Button',
        props: {
            text: String,
            color: String
        },
        methods: {
            onClick() {
                console.log("Followed")
                //this.color = "Grey"
            }
        }
    }
</script>
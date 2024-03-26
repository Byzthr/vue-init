<template>
    <button @click="onClick()" class="btn" :style="{ background: color }">{{ text }}</button>
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
                console.log("Clikkkk")
                //this.color = "Grey"
            }
        }
    }
</script>
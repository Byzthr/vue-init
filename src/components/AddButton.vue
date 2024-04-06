<template>
    <button
        @click="onClick"
        :class="{ 'added' : userAdded }"
        class="addButton btn">
        <i :class="icon"></i> {{ text }}
    </button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        userAdded: {
            type: Boolean,
            required: true,
        }    
    },
    data() {
        return {
            icon: this.userAdded ? "0" : "fa-solid fa-user-plus",
            text: this.userAdded ?  "Added" : "Add",
        }
    },
    watch: {
        userAdded: function() {
            this.icon = this.userAdded ? "0" : "fa-solid fa-user-plus"
            this.text = this.userAdded ?  "Added" : "Add"
        }
    },
    methods: {
        onClick() {
            this.$emit("addUser")
        }
    }
}
</script>

<style scoped>
.addButton {
    background: lightblue;
}

.added {
    color: black;
    background: lightgrey;
}
</style>

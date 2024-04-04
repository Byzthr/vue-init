<template>
    <div @dblclick="$emit('toggle-unchecked', notification.id)" :class="[notification.unchecked ? 'unchecked' : '', 'notification']">
        <h3>
            {{ notification.text }}
            <i @click="onDelete(notification.id)" class="far fa-trash-can"></i>
        </h3>
        <p>{{ notification.date }}</p>
    </div>
</template>

<script>
export default {
    name: "Notification",
    props: {
        notification: Object,
    },
    methods: {
        onDelete(id) {
            // console.log("Deleting notification with ID:", id)
            this.$emit('delete-notification', id)
        }
    }
}
</script>

<style>
.notification {
    border-radius: .3rem;
    background: rgb(232, 232, 232);
    margin: 1rem;
    padding: 1rem;
    cursor: pointer;
}
.notification.unchecked {
    border-left: .2rem solid green;
}

.notification h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.far {
    color: red;
}
</style>

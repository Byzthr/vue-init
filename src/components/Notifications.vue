<template>
    <div class="notifications" >
        <Notification
            @delete-notification="$emit('delete-notification', notification.id)" 
            @toggle-unchecked="$emit('toggle-unchecked', notification.id)"
            :key="notification.id" v-for="notification in notifications" :notification="notification"
        />
    </div>
</template>

<script>
import Notification from './Notification'

export default {
    name: "Notifications",
    props: {
        notifications: Array,
    },
    components: { 
        Notification,
    },
    emits: ["delete-notification", "toggle-unchecked"],
}
</script>
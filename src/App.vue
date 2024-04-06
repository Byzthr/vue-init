<template>
  <div class="container">
    <Header desc="The Tamed Team Project"/>
    <AddButton
      :userAdded="addedUser"
      @addUser="toggleAdded"/>
    <Button text="Message" color="lightgreen" />
    <Button text="PBs" color="orange" />
  </div>
  <NewPost
    v-show="showNewPost"
    @new-post="newPost"/>
  <Notifications
    v-show="showNotifications"
    @delete-notification="deleteNotification"
    @toggle-unchecked="toggleUnchecked"
    :notifications="notifications" />
  <Posts
    :posts="posts" />
  <Footer 
    @toProfile="toProfile"
    @toNotifications="toNotifications"
    @toNewPost="toNewPost" />
</template>

<script>
import Header from './components/Header'
import Button from './components/Button'
import AddButton from './components/AddButton'
import Notifications from './components/Notifications'
import NewPost from './components/NewPost'
import Posts from './components/Posts'
import Footer from './components/Footer'

import artistic_portrait from '@/assets/Artistic_portrait.jpeg'
import subbaImg from '@/assets/Subba.jpeg'
import CV1flip from '@/assets/CV1flip.jpg'
import e60 from '@/assets/E60.jpeg'

export default {
  name: 'App',
  components: {
    Header,
    Button,
    AddButton,
    Notifications,
    NewPost,
    Posts,
    Footer,
  },
  data() {
    return {
      notifications: [],
      posts: [],
      addedUser: false,
      showNotifications: false,
      showNewPost: false,
    }
  },
  methods: {
    toggleAdded() {
      this.addedUser = !this.addedUser
    },
    toProfile() {
      this.showNotifications = false
      this.showNewPost = false
    },
    toNotifications() {
      this.showNotifications = true
      this.showNewPost = false
    },
    toNewPost() {
      this.showNotifications = false
      this.showNewPost = true
    },
    newPost(post) {
      this.posts = [...this.posts, post]
    },
    deleteNotification(id) {
      if (confirm("Delete notification?")) {
        this.notifications = this.notifications.filter((notification) => notification.id !== id)
      }
    },

    toggleUnchecked(id) {
      this.notifications = this.notifications.map((notification) =>
        notification.id === id ?
        { ...notification, unchecked: !notification.unchecked} : notification)
    }
  },
  created() {
    this.notifications = [
      {
        id: 1,
        type: "New message",
        text: "New message from x",
        date: "March 19th at 11.30",
        unchecked: true,
      },
      {
        id: 2,
        type: "New follower",
        text: "X startewd following you",
        date: "March 19th at 12.30",
        unchecked: false,
      },
      {
        id: 3,
        type: "New message",
        text: "New message from y",
        date: "March 19th at 13.00",
        unchecked: false,
      },
      {
        id: 4,
        type: "New PB",
        text: "Your friend X just broke his PB!!",
        date: "March 19th at 13.15",
        unchecked: false,
      },
    ],
    this.posts = [
      {
        id: 1,
        type: "New PR",
        image: artistic_portrait,
        date: "March 19th at 11.30",
        caption: "BESST YET",
      },
      {
        id: 2,
        type: "Crazy Lift",
        image: subbaImg,
        date: "March 19th at 11.30",
        caption: "La virgen",
      },
      {
        id: 3,
        type: "Meeting",
        image: CV1flip,
        date: "March 19th at 11.30",
        caption: "Mis broders",
      },
      {
        id: 4,
        type: "Meeting",
        image: e60,
        date: "March 19th at 11.30",
        caption: "Mis sisters",
      },
    ]
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid rgb(110, 110, 110);
  padding: 30px;
  border-radius: 5px;
  background: rgb(232, 232, 232);
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>

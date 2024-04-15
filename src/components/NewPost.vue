<template>
    <form @submit="onSubmit" class="post-form">
        <h3>New post</h3>
        <div class="form-control">
            <input type="radio" id="PR" name="post" value="PR" v-model="type">
            <label class="post-radio" for="PR">New PR</label>
            <input type="radio" id="crazy" name="post" value="crazy" v-model="type">
            <label class="post-radio" for="crazy">Crazy lift</label>
            <input type="radio" id="meet" name="post" value="meet" v-model="type">
            <label class="post-radio" for="meet">Meeting</label>
        </div>
        <div class="form-control">
            <label for="post-image">Photo</label>
            <input
                type="file"
                accept="image/*"
                class="post-media"
                @change="uploadImage">
        </div>
        <div class="form-control">
            <label for="post-caption">Caption</label>
            <input type="text" id="post-caption" placeholder="Caption" v-model="caption">
        </div>
        <input class="btn" type="submit" value="Post"> 
    </form>
</template>

<script>
export default {
    name: "newPost",
    data() {
        return {
            id: undefined,
            type: '',
            caption: '',
            image: undefined,
            date: ''
        }
    },
    methods: {
        uploadImage(e) {
            const file = e.target.files[0]
            this.image = file
        },
        onSubmit(e) {
            e.preventDefault()

            if(!this.caption) {
                alert("Please add caption")
                return
            }

            const newPost = {
                id: Math.floor(Math.random() * 100000),
                type: this.type,
                caption: this.caption,
                // image: this.image,
                image: "E60.jpeg",
                date: Date.now()
            }
            this.$emit("newPost", newPost)
        }
    }
}
</script>

<style scoped>
.post-form {
    background: lightblue;
    margin: 1rem;
    padding: 1rem;
}

.form-control {
    display: flex;
    justify-content: center;
    /* flex-direction: column; */
}

input[type="radio"] {
    display: none;
}

label {
    padding: .2rem;
    border-radius: .2rem;
    margin: .3rem;
    cursor: pointer;
}

input[type="radio"]:checked + label {
    color: aliceblue;
    background: rgb(88, 88, 255);
}
</style>

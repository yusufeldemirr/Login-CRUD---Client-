<template>
<div class="container">
    <div v-for="post in posts" :key="post._id" class="card my-5">
        <div class="card-content">
         <img src="https://img.myloview.com/posters/default-avatar-profile-flat-icon-social-media-user-vector-portrait-of-unknown-a-human-image-400-209987471.jpg" width="90">
          <div class="media">
            <div class="media-content">
              <br>
              <p class="title is-4">İsim:{{post.firstname}}</p>
            </div>
          </div>
      
          <div class="content">
            {{ post.content}} 
            <p />
            <strong >Soyisim: {{post.lastname}}</strong>
          </div>
        </div>
        <div class="card">
            <footer class="card-footer">
              <button @click="editPost(post._id)" class="card-footer-item button is-warning">Düzenle</button>
              <button @click="removePost(post._id)" class="card-footer-item button is-danger">Sil</button>
            </footer>
          </div>
      </div>
</div>

</template>

<script>
import {ref, onMounted} from "vue"
import { useRouter } from "vue-router"
export default{
    setup() {
      const router= useRouter()
        const posts = ref([])

        const API_URL = "http://localhost:3000/posts"

        onMounted(()=> {
            getPosts()
        })

        async function getPosts() {
            try {
                const response = await fetch(API_URL)
                const json = await response.json()
                posts.value = json
            } catch (error) {
                console.log(error)
            }

        }

        async function removePost(_id){
            const response = await fetch(API_URL + "/" + _id,{
                method:"DELETE",
            })
            getPosts() 
        }

        async function editPost(_id){
          router.push({
            name: "Update",
            params: {
              id: _id,
            },
          })
        }
        return {
            posts,
            removePost,
            editPost,
        }
    },
}
</script>

<style>

</style>
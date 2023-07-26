<template>
<post-form :post="post" :submitForm="updatePost"></post-form>
</template>

<script>
import PostForm from "../components/PostForm.vue"
import {useRouter, useRoute} from "vue-router"
import {ref, onMounted} from "vue"

export default{
    components:{
        PostForm,
    },
    setup(){
        const router= useRouter()
        const route = useRoute()
        const API_URL = "http://localhost:3000/posts"

        const post = ref({
            firstname: "",
            lastname:"",
            email:"",
            password:"",
        })

        onMounted(()=> {
            getPost()
        })

        async function getPost() {
            const {id} = route.params
            const response = await fetch(API_URL + "/" + id,)
            const json = await response.json()
            post.value = json
        }

        async function updatePost(){
            const { id } = route.params
            const response = await fetch(API_URL + "/" + id,{
                method: "PUT",
                headers: {
                    "content-type": "application/json",
                },
                body: JSON.stringify({
                    firstname: post.value.firstname,
                    lastname: post.value.lastname,
                    email: post.value.email,
                    password: post.value.password
                })
            })
            const json = await response.json()
            router.push({
                name:"home",
            })
        }
        return{
            post,
            updatePost,
        }
    }
}
</script>

<style></style>
<template>
<PostForm :post="post" :submitForm="createPost"/>
</template>

<script>
import PostForm from "../components/PostForm.vue"
import {reactive} from "vue" 
import {useRouter} from "vue-router"
export default{
    components: {
        PostForm,
    },
    setup (){
        const API_URL = "http://localhost:3000/posts"
        const router = useRouter()

        const post = reactive({
            firstname:"",
            lastname:"",
            email:"",
            password:""

        })

        async function createPost(){
            const response = await fetch(API_URL,{
                method: "POST",
                headers:{
                    "content-type": "application/json"
                },
                body: JSON.stringify({
                    firstname: post.firstname,
                    lastname: post.lastname,
                    email: post.email,
                    password: post.password
                })

            })
            const json = await response.json()
            router.push({
                name: "home",
            })


            }
            return {
            post,
            createPost,
        }
        },

    }

</script>

<style></style>
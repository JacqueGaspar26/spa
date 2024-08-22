<template>
    <div class="p-4">
        <div v-if="post.id" class="p-4">
            <h2 class="text-xl font-bold uppercase">
                {{ post.title }}
            </h2>
            <small class="text-blue-500">
                Id del autor: {{ post.userId }}
            </small>
            <p class="text-gray-700">
                {{ post.body }}
            </p>
        </div>

        <div v-else class="p-12">
            <p class="text-xl font-mono ">Cargando...</p>
        </div>
    </div>
</template>

<script>
import axios from "axios";
const API_URL = "https://jsonplaceholder.typicode.com/posts";

export default {
    name: "PostPage",
    props: ["id"],
    data() {
        return {
            post: {},
        };
    },

    created() {
        this.getPost();
    },

    methods: {
        getPost() {
            axios.get(`${API_URL}/${this.id}`).then((response) => {
                    this.post = response.data;
                    console.log(this.post);
                });
        },
    },

    watch:{
        id(){
            this.getPost();
        }
    }
};

</script>
<template>
    <h1>Listado de Posts <button class="btn btn-primary">Estilado con Boostrap</button></h1>
    <ul class="post-list">
        <li v-for="post  in posts" :key="post.id">
            {{ post.title }}
        </li>
    </ul>
</template>

<script lang="ts" setup>
import { defineComponent,Ref, onMounted } from 'vue'
import PostService from '@/services/PostService'
import IPost from '@/interfaces/IPost'

/*export default defineComponent({
    name : 'PostList',
    setup() {
        const service = new PostService()
        const posts = service.getPost()
        onMounted( async () =>{
            await service.fetchAll()
        } )

        return {posts}
    }
})*/

    const service = new PostService()
    const posts:Ref<Array<IPost>> = service.getPost()
    onMounted( async () =>{
        await service.fetchAll()
    })
        
    
</script>

<style lang="scss" scoped>
    .post-list {
        width: 95vw;
        height: 75px;
        padding: 20px;
        list-style-type: none;
        li {
            padding: 10px;
            width: 100%;
            border: 1px solid #ccc;
            color: $blue
        }
        li:hover {
            background-color: darken($color: #000000, $amount: 10%);
        }
    }
</style>
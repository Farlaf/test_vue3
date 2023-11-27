<template>
    <h1>Посты</h1>
    <my-button
        @click="makeDialogVisible"
    >Добавить пост</my-button>

    <my-dialog v-model:show="dialogVisible">
        <post-form
            @create="createPost"
        />
    </my-dialog>
    <post-list
        :posts="posts"
        @remove="removePost"
        v-if="!isPostsLoading"
    />
    <div v-else>Идет загрузка</div>
</template>

<script>
import axios from 'axios'
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";

export default {
    components: {
        PostList, PostForm
    },
    data() {
        return {
            posts: [],
            title: '',
            body: '',
            dialogVisible: false,
            isPostsLoading: false,
        }
    },
    methods: {
        createPost(post) {
            this.posts.push(post);
            this.dialogVisible = false;
        },
        removePost(post) {
            this.posts = this.posts.filter(p => p.id != post.id)
        },
        makeDialogVisible() {
            this.dialogVisible = true;
        },
        async fetchPosts() {
            try {
                this.isPostsLoading = true;
                const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=5');
                this.posts = response .data;
                this.isPostsLoading = false;
            } catch(e) {
                alert('Error')
            }
        },
    },
    mounted() {
        this.fetchPosts();
    }
}
</script>

<style>
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

body {
    padding: 20px;
}
</style>

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
    />
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";

export default {
    components: {
        PostList, PostForm
    },
    data() {
        return {
            posts: [{
                    id: 1,
                    title: 'JS #1',
                    body: 'JS - язык на каждый день'
                },
                {
                    id: 2,
                    title: 'JS #2',
                    body: 'JS -  на каждый день'
                },
                {
                    id: 3,
                    title: 'JS #3',
                    body: 'JS - язык на  день'
                }
            ],
            title: '',
            body: '',
            dialogVisible: false
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
        }
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

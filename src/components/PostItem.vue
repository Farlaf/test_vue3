<template>
    <article class="post">
        <div>
            <h3>{{ post.title }}</h3>
            <p>{{ post.body }}</p>
        </div>
        <div class="post__controls">
            <my-button
                @click="$emit('remove', post)"
            >Удалить</my-button>
        </div>
    </article>
</template>

<script>
    export default {
        props: {
            post: {
                type: Object,
                required: true
            }
        }
    }
</script>

<style scoped>
    .post {
        padding: 15px;
        border: 1px solid red;
        margin-top: 15px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>

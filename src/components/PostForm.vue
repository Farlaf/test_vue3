<template>
    <form @submit.prevent>
        <h4>Добавить пост</h4>
        <my-input
            v-model="post.title"
            placeholder="Название"
        />
        <my-input
            v-model="post.body"
            placeholder="Описание"
        />
        <my-button @click="createPost">Создать</my-button>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                post: {
                    title: '',
                    body: ''
                }
            }
        },
        methods: {
            createPost() {
                this.post.id = Date.now();
                this.$emit('create', this.post)
                this.post = {
                    title: '',
                    body: ''
                }

            }
        },
    }
</script>

<style scoped>
</style>

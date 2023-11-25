<template>
    <input
        :value = "modelValue"
        @input = "updateInput"
        type="text">
</template>

<script>
export default {
    name: 'my-input',
    props: {
        modelValue: [String, Number]
    },
    methods: {
        updateInput(e) {
            this.$emit('update:modelValue', e.target.value)
        }
    }
}
</script>

<style scoped>
    input {
        display: block;
        max-width: 450px;
        padding: 10px 6px;
        margin-bottom: 10px;
    }
</style>

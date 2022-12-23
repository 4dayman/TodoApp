<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit">Create</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        onSubmit() {
            // console.log('submit', this.title)
            if (this.title.trim()) {
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false
                }
                this.$emit('add-todo', newTodo)
                this.title = '' // удаляет текст из инпута
            }
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }
    input {
        height: 30px;
        width: 90%;
        margin-bottom: 10px;
    }
    button{
        background: rgb(42, 161, 88);
        border: none;
        color: #fff;
        min-width: 90px;
        border-radius: 5px;
    }
</style>
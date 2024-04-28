<template>
    <form class="form" @submit.prevent="submitHandler">
        <input type="text" class="form__input" v-model="taskTitle">
    </form>
</template>

<script>
export default {
    data() {
        return {
            taskTitle: ""
        }
    },
    methods: {
        submitHandler() {
            this.$emit("submitHandler", this.taskTitle)
            this.taskTitle = ""
        }
    }
}
</script>

<style lang="scss">
.form {
    margin: 15px 0;
    max-width: 400px;
    width: 100%;

    &__input {
        border: 1px solid black;
        border-radius: 5px;
        padding: 5px;
        outline: none;
        font-size: 18px;
        width: 100%;

    }
}
</style>
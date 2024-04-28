<template>
    <div class="task">
        <h2 class="task-title">{{ task.title }}</h2>
        <button class="home__list-del " @click="deleteTask(index)">DELETE</button>
    </div>
</template>

<script>
export default {
    props: ["task", "index"],
    methods: {
        deleteTask(idx) {
            this.$emit("deleteTask", idx)
        }
    }
}
</script>


<style lang="scss">
.task {
    border: 1px solid black;
    border-radius: 5px;
    padding: 20px;

    &:not(_:last-child) {
        margin-bottom: 20px;
    }

    &__title {
        margin-bottom: 20px;
    }
}
</style>
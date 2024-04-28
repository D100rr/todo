<template>
    <div class="list" v-if="tasks.length">
        <myTask v-for="(task, idx) of tasks" :key="task.id" :task="task" :index="idx" @deleteTask="$emit('deleteTask', idx)" />
    </div>
</template>

<script>
import myTask from "@/components/myTask.vue"

export default {
    props: ["tasks"],
    components: {
        myTask
    }
}
</script>


<style lang="scss">
  .list {
    max-width: 600px;
    width: 100%;
  }
</style>
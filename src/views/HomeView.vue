<template>
  <div class="home">
    <h1 class="home__title">TODO APP</h1>
    <myForm @submitHandler="addTask" />
    <myList :tasks="tasks" @deleteTask="deleteTask" v-if="tasks.length" />
    <h2 class="home__noTask" v-else> Задач пока нету </h2>
  </div>
</template>

<script>
import myForm from "@/components/myForm.vue"
import myList from "@/components/myList.vue"

export default {
  data() {
    return {
      tasks: [
        { id: 1, title: 'Title 1' },
        { id: 2, title: 'Title 2' },
        { id: 3, title: 'Title 3' }
      ]
    }
  },
  methods: {
    addTask(title) {
      if (title.trim() === "") return

      const task = {
        id: Date.now(),
        title
      }

      this.tasks.push(task)
      this.setStorage()
    },

    deleteTask(idx) {
      this.tasks.splice(idx, 1)
      this.setStorage()
    },
    setStorage() {
      localStorage.setItem("tasks", JSON.stringify(this.tasks))
    }
  },
  components: {
    myForm,
    myList
  },
  mounted() {
    this.tasks = JSON.parse(localStorage.getItem("tasks")) || this.tasks
  }
}
</script>

<style lang="scss" scoped>
.home {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;

  &__title {
    text-align: center;

  }
}
</style>
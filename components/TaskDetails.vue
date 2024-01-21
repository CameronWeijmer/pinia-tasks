<template>
    <div class="task">
        <h3>{{ task.title }}</h3>
        <div class="icons">
            <Icon @click="taskStore.toggleFav(task.id)" class="i" name="uil:heart" color="black" />
            <Icon :class="{ active: task.isFav }" @click="taskStore.deleteTask(task.id)" class="i" name="uil:trash-alt"
                color="black" />
        </div>
    </div>
</template>

<script>
export default {
    props: ["task"]
}
</script>

<script setup>
const taskStore = useTaskStore()
</script>
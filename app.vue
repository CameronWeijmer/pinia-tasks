<template>
    <div>
        <header>
            <img src="./assets/pinia_logo.svg" alt="Pinia Logo">
            <h1>Pinia Tasks</h1>
        </header>

        <!-- new Task form -->

        <div class="new-class-form">
            <TaskForm />
        </div>

        <!-- filter -->
        <nav class="filter">
            <button @click="filter = 'all'">All tasks</button>
            <button @click="filter = 'favs'">Fav tasks</button>
        </nav>

        <!-- loading -->
        <div class="loading" v-if="loading">Loading tasks...</div>

        <!-- task list -->
        <div class="task-list" v-if="filter === 'all'">
            <p>You have {{ totalCount }} tasks left to do</p>
            <div v-for="task in tasks">
                <TaskDetails :task="task" />
            </div>
        </div>
        <div class="task-list" v-if="filter === 'favs'">
            <p>You have {{ favCount }} favs left to do</p>

            <div v-for="task in favs">
                <TaskDetails :task="task" />
            </div>
        </div>

        <button @click="taskStore.$reset">Reset state</button>

    </div>
</template>

<script setup>
const taskStore = useTaskStore()

const { tasks, loading, favs, totalCount, favCount } = storeToRefs(taskStore)

const filter = ref("all")

// fetch tasks
taskStore.getTasks()
</script>
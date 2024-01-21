<template>
    <div class="task">
        <h3>{{ task.title }}</h3>
        <div class="icons">
            <Icon class="i" name="uil:heart" color="black" />
            <Icon class="i" name="uil:trash-alt" color="black" />
        </div>
    </div>
</template>

<script>

export default {
    props: ["task"]
}

</script>
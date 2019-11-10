<template>

    <div>
        <div v-if="open">
            <span id="add-course">
            <input class="input" type="text" placeholder="Course title" id="title">
            <input class="input" type="number" min="1" max="8" placeholder="Semester" id="semester">
            <input class="input" type="number" min="0" max="100" placeholder="Grade" id="grade">
            <button class="green-button" id="save-course">Save</button>
            <button class="grey-button" id="cancel-course" @click="open = false">Cancel</button>
        </span>
        </div>
        <div v-else>
            <button id="add-course-button" class="blue-button" @click="open = true">+</button>
            <h1>Hel</h1>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Courses_add_course"
    }
</script>

<style scoped>

</style>

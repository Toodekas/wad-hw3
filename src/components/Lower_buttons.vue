<template>
    <div class="controls">
        <div v-if="open">
            <Courses_view/>
            <button id="profile-button" class="pill " @click="open = false">Profile</button>
            <button id="courses-button" class="pill active" @click="open = true">Courses</button>
        </div>
        <div v-else>
            <div id="content">
                <Profile_view/>
            </div>
            <button id="profile-button" class="pill active" @click="open = false">Profile</button>
            <button id="courses-button" class="pill" @click="open = true">Courses</button>
        </div>
    </div>
</template>

<script>
    import Profile_view from "./Profile_view";
    import Courses_view from "./Courses_view";
    export default {
        name: "Lower_buttons",
        data: () => {
            return {
                title: "",
                open: false
            }
        },
        components: {
            Profile_view,
            Courses_view
        }
    }
</script>

<style scoped>

</style>

<template>
    <div id="profile-container" class="tab active">
        <div id="profile">
            <div class="avatar">
                <img src="./assets/me.png" id="picture" alt="My picture">
            </div>
            <div class="info">
                <ul>
                    <li id="name">John Doe</li>
                    <li id="birthdate">11/10/1990</li>
                    <li id="faculty">Software Engineering</li>
                </ul>
            </div>
            <div id="gpa">
                <strong>{{gpaVal}}</strong>
                <button v-on:click="callGPA"></button>
            </div>
            <div class="clear-fix"></div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Profile_view",
        data: () => {
            return {
                gpaVal: localStorage.gpaVal
            }
        },
        methods: {
            callGPA() {
                localStorage.gpaVal = 1000;
            }
        },
        mounted() {
            localStorage.gpaVal = 2.8;
        }
    }
</script>

<style scoped>

</style>

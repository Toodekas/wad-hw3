<template>

    <div id="courses-container" class="tab">
        <h1 class="title">Courses</h1>
        <table id="courses">
            <thead>
            <tr>
                <th>#</th>
                <th>Course Title</th>
                <th>Semester</th>
                <th>Grade</th>
            </tr>
            </thead>
            <tbody>
            <tr>
                <td>1</td>
                <td>Agile software development</td>
                <td>1</td>
                <td>82</td>
            </tr>
            <tr>
                <td>2</td>
                <td>System modeling</td>
                <td>1</td>
                <td>85</td>
            </tr>
            <tr>
                <td>3</td>
                <td>Object-oriented programming</td>
                <td>2</td>
                <td>99</td>
            </tr>
            <tr>
                <td>4</td>
                <td>Estonian language Level A2</td>
                <td>2</td>
                <td>65</td>
            </tr>
            </tbody>
        </table>
        <br>
        <br>
        <div v-if="open">
            <input class="input" type="text" placeholder="Course title" id="title">
            <input class="input" type="number" min="1" max="8" placeholder="Semester" id="semester">
            <input class="input" type="number" min="0" max="100" placeholder="Grade" id="grade">
            <button class="green-button" id="save-course">Save</button>
            <button class="grey-button" id="cancel-course" @click="open = false">Cancel</button>
        </div>
        <div v-else>
            <button id="add-course-button" class="blue-button" @click="open = true">+</button>
        </div>
        <div id="deleteme">
            <button v-on:click="getCoursesPoints"></button>
            <h1 id="test1"></h1>
        </div>
        <br>
        <br>

    </div>

</template>

<script>

    export default {
        name: "Courses_view",
        data: () => {
            return {
                title: "",
                open: false
            }
        },
        methods: {
          calcGPApoints : function(x) {
              if (x > 90) {
                  return 4;
              } else if (x > 80) {
                  return 3;
              } else if (x > 70) {
                  return 2;
              } else if (x > 60) {
                  return 1;
              } else if (x > 50) {
                  return 0.5;
              } else {
                  return 0;
              }
          },
          getCoursesPoints : function() {
              //$('#courses tr td').eq(4).val();
              //let test = $('#courses tr td').eq(4).val();
              //this.$("#test1").text(test);
              localStorage.item = document.getElementById("courses");
              alert(localStorage.item);
              return localStorage.item;
          }
        }
    }
</script>


<style scoped>

</style>

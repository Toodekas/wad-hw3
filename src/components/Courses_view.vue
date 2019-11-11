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
            <tr v-for="(obj,index) in objects" v-bind:key="index">
                <td>{{index+1}}</td>
                <td>{{obj.name}}</td>
                <td>{{obj.semester}}</td>
                <td>{{obj.grade}}</td>
            </tr>
            <!--
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
            -->
            </tbody>
        </table>
        <br>
        <br>
        <div v-if="open">
            <input v-model="inputName" class="input" type="text" placeholder="Course title" id="title">
            <input v-model="inputSemester" class="input" type="number" min="1" max="8" placeholder="Semester" id="semester">
            <input v-model="inputGrade" class="input" type="number" min="0" max="100" placeholder="Grade" id="grade">
            <button class="green-button" id="save-course" v-on:click="() => { addNewRow(); open = false; inputName = ''; inputSemester = ''; inputGrade = ''; }">Save</button>
            <button class="grey-button" id="cancel-course" @click="() => { open = false; inputName = ''; inputSemester = ''; inputGrade = '' }">Cancel</button>
        </div>
        <div v-else>
            <button id="add-course-button" class="blue-button" @click="open = true">+</button>
        </div>




        <br>
        <br>

    </div>

</template>

<script>

    export default {
        name: "Courses_view",
        data:
            () => {
            return {
                title: "",
                open: false,
                inputName: '',
                inputSemester: '',
                inputGrade: '',
                objects: [
                    {
                        name: "Agile software development",
                        semester: 1,
                        grade: 82
                    },
                    {
                        name: "System modeling",
                        semester: 1,
                        grade: 85
                    },
                    {
                        name: "Object-oriented programming",
                        semester: 2,
                        grade: 99
                    },
                    {
                        name: "Estonian language Level A2",
                        semester: 2,
                        grade: 65
                    }
                ]
            }
        },
        methods: {
            addNewRow : function () {
              this.objects.push({name: this.inputName, semester: this.inputSemester, grade: this.inputGrade});
              this.getGPA();
            },
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
          getGPA : function() {
                let sum = 0;
                let counter = 0;
              for (let obj in this.objects) {
                    sum = sum + this.calcGPApoints(parseInt(this.objects[obj].grade));
                    counter = counter + 1;
              }
              localStorage.gpaVal = Math.round((sum/counter) * 10) / 10;
          }
        },
        mounted() {
            this.getGPA();
        }
    }
</script>


<style scoped>

</style>

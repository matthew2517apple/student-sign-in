<template>
    <div>
        <div class="card student-list m-2 p-2">
            <h4 class="card-title">Students</h4>
            <div id="student-table">
                <table class="table">
                    <tr>
                        <th>Name</th>
                        <th>StarID</th>
                        <th>Present?</th>
                    </tr>

                    <tr v-for="student in students" v-bind:class="'present-'+student.present">
                        <td> {{student.name}} </td>
                        <td> {{student.starID}} </td>
                        <td> <input type="checkbox"
                                    v-model="student.present"
                                    @change="checked(student)">
                        </td>

                    </tr>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name: 'StudentTable',
    props: {
        students: Array
    },
    methods: {
        checked(student) {
            this.$emit('student-present', student)
        }
    }
}
</script>

<style>

#student-table {
    max-height: 500px;
    overflow: scroll;
}

.present-true {
    font-style: italic;
    font-size: 20px;
    color: gray;
}

.present-false {
    font-size: 30px;
    color: darkred;
}
</style>
<template>
    <div>
        <h3>Person List</h3>
        <ul>
            <li v-for="(person, index) in personList" :key="index">
                <img v-if="person.photoUrl" :src="person.photoUrl" alt="person photo" width="50"
                    style="vertical-align: middle; margin-right: 10px;" />
                <strong>{{ person.name }}</strong> - Age: {{ person.age }}, BMI: {{ person.bmi }}, Category: {{
                    person.category }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'PersonList',
    props: {
        personList: {
            type: Array,
            required: true
        }
    }
};
</script>
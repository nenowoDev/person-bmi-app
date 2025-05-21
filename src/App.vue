<template>
    <div class="container">
        <h1>Person BMI Web App</h1>

        <nav class="main-nav">
            <a href="#">Add Person</a> |
            <a href="#">View All</a> |
            <a href="#">View One</a> |
            <a href="#">Edit</a> |
            <a href="#">Delete</a>
        </nav>

    </div>
    <AddPerson></AddPerson>
    <ListPersons></ListPersons>
    <ViewPerson></ViewPerson>
    <EditPerson></EditPerson>
    <DeletePerson></DeletePerson>
    <BmiText></BmiText>
</template>

<script>
import AddPerson from './components/AddPerson.vue';
import BmiText from './components/BmiText.vue';
import DeletePerson from './components/DeletePerson.vue';
import EditPerson from './components/EditPerson.vue';
import ListPersons from './components/ListPersons.vue';
import ViewPerson from './components/ViewPerson.vue';

export default {
    name: 'App',
    components: {
        AddPerson,
        BmiText,
        DeletePerson,
        EditPerson,
        ListPersons,
        ViewPerson
    }
}
</script>

<style></style>

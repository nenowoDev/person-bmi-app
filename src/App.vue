<template>
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

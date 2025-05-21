<template>
    <div class="container">
        <h1>Person BMI Web App</h1>

        <nav class="main-nav">
            <RouterLink to="addperson">Add Person</RouterLink> |
            <RouterLink to="listperson">View All</RouterLink> |
            <RouterLink to="viewperson">View One</RouterLink> |
            <RouterLink to="editperson">Edit</RouterLink> |
            <RouterLink to="deleteperson">Delete</RouterLink>
        </nav>

    </div>
    <RouterView @person-added="handleAddPerson" :personList ='personList'  @update-person="handleUpdatePerson" @delete-person="handleDeletePerson"></RouterView>
    <!-- <RouterView></RouterView> -->
    <!-- <AddPerson @person-added="handleAddPerson"></AddPerson>
    <ListPersons :personList ='personList'></ListPersons> 
    <ViewPerson :personList ='personList'></ViewPerson>
<EditPerson :personList="personList" @update-person="handleUpdatePerson" />
    <DeletePerson></DeletePerson>
    <BmiText :person-list="personList"></BmiText> -->
    
</template>

<script>
// import AddPerson from './components/AddPerson.vue';
// import BmiText from './components/BmiText.vue';
// import DeletePerson from './components/DeletePerson.vue';
// import EditPerson from './components/EditPerson.vue';
// import ListPersons from './components/ListPersons.vue';
// import ViewPerson from './components/ViewPerson.vue';

export default {
    name: 'App',
    components: {
        // AddPerson,
        // BmiText,
        // DeletePerson,
        // EditPerson,
        // ListPersons,
        // ViewPerson
    },
    data() {
        return {
            personList: [
                {
                    name: "Hassan",
                    yob: 1995,
                    age: new Date().getFullYear() - 1995,
                    weight: 68,
                    height: 175,
                    bmi: (68 / ((175 / 100) ** 2)).toFixed(2),
                    category: 't.b.c',
                    photoUrl: "https://randomuser.me/api/portraits/men/44.jpg"
                },
                {
                    name: "Siti",
                    yob: 2000,
                    age: new Date().getFullYear() - 2000,
                    weight: 52,
                    height: 160,
                    bmi: (52 / ((160 / 100) ** 2)).toFixed(2),
                    category: 'normal',
                    photoUrl: "https://randomuser.me/api/portraits/women/3.jpg"
                }
            ],
        }
    },
    methods: {
        handleAddPerson(entry)
        {
            this.personList.push(entry)
        },
         handleUpdatePerson(index, updatedPerson) {
         this.personList.splice(index, 1, updatedPerson); // ✅ update from child
  },
         handleDeletePerson(index){
            this.personList.splice(index,1)
         }
    },
 
}



</script>

<style></style>

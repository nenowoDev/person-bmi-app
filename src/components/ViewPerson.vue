<template>
    <h3>View One Person</h3>
    <input type="number" id="indexInput" v-model.number="indexInput" placeholder="Enter index" />
    <div id="onePersonView" class="detail-box">
           <template v-if="selectedPerson">
                <p>Name: {{ selectedPerson.name }}</p>
                <p>Year of Birth: {{ selectedPerson.yob }}</p>
                <p>Age: {{ selectedPerson.age }}</p>
                <p>Weight: {{ selectedPerson.weight }} kg</p>
                <p>Height: {{ selectedPerson.height }} cm</p>
                <p>BMI: {{ selectedPerson.bmi }}</p>
                <img v-if="selectedPerson.photoUrl" :src="selectedPerson.photoUrl" alt="Person photo" class="person-photo">
            </template>
        <em v-else>No person at that index</em>
    </div>

</template>
<script>
 export default{
    name:"viewPerson",
    props:{
        personList:{
            type:Array,
            required:true
        }
    },
    data(){
        return{
            indexInput:'',
            selectedPerson:''
        }
    },
    watch: {
        indexInput: {
            handler: 'displayByIndex',
            immediate: true
        }
    },
    methods:{
        displayByindex(){
          if(this.indexInput>0 && this.indexInput<this.personList.length)
          {
            this.selectedPerson = this.personList[this.indexInput]
          }else{
            this.selectedPerson=null;
          }
        

        }
    }
 }
</script>

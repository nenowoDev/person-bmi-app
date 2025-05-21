<template>
    <h3>View One Person</h3>
    <input type="number" id="indexInput" v-model.number="indexInput" placeholder="Enter index" />
    <div id="onePersonView" class="detail-box">
        <template v-if="selectedPerson">
            <p>Name : {{ selectedPerson.name }}</p>
            <p>Name : {{ selectedPerson.yob }}</p>
            <p>Name : {{ selectedPerson.age }}</p>
            <p>Name : {{ selectedPerson.weight }}</p>
            <p>Name : {{ selectedPerson.height }}</p>
            <p>Name : {{ selectedPerson.bmi }}</p>
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

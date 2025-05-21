<template>
    <h3>View One Person</h3>
    <input type="number" id="indexInput" v-model.number="indexInput" placeholder="Enter index" />
    <div id="onePersonView" class="detail-box">
        <em>No person at that index</em>
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
            indexInput:''
        }
    },
    methods:{
        displayByindex(){
          this.personList.forEach((item)=>{
            if(item == this.indexInput)
          }
        )

        }
    }
 }
</script>

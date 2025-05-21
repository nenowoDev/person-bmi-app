<template>
    <h3>Delete Person by Index</h3>
    <input type="number" id="deleteIndex" v-model="deleteIndex" placeholder="Enter index to delete" />
    <div id="deleteFeedback" class="feedback">
        <em v-if="!isvalidIndex"> Enter a valid index to delete</em>
        <em v-else> Ready to delete:{{ personList[deleteIndex].name}}</em>
        <button v-if="isValidIndex" @click="deletePerson">Delete Person</button>

    </div>

</template>
<script>
export default{
    data(){
        return{
            deleteIndex:null
        }
    },
    props:{
        personList:{
            type:Array,
            retuired:true
        }
    },
    computed:{
      isvalidIndex(){
        return this.deleteIndex !== null && 
                  this.deleteIndex >= 0 && 
                  this.deleteIndex < this.personList.length;
      }
    },
    methods:{
         deletePerson(){
         if(this.isvalidIndex){
            if(confirm(`are you sure want to delete ${this.personList[this.deleteIndex].name}`)){
                this.$emit('delete-person',this.deleteIndex)
                this.deleteIndex = null
            }
        }
       }
    }
}
</script>
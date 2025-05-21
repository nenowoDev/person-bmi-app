<template>
    <h3>Add Person</h3>
    <form  @submit.prevent = "submitForm">
        Fullname : <input v-model="fullName" placeholder="Name" required />
        Year Born : <input v-model.number="yearBorn" placeholder="yyyy" required />
        Weight : <input v-model.number="weight" placeholder="Weight (kg)" required />
        Height : <input v-model.number="height" placeholder="Height (cm)" required />
        Photo URL : <input type="text" id="photoUrl" placeholder="Image URL" />
        <button type="submit">Add Person</button>
    </form>
</template>
<style>

</style>
<script>
export default{
    name:"addPerson",
    data(){
        return{
            fullName:'',
            yearBorn:'',
            weight:'',
            height:''

        };
       

    },
     methods : {
            submitForm(){
             const bmi = this.weight / ((this.height / 100) ** 2); // assuming height in cm
             this.$emit('add-person',{
                fullName : this.fullName,
                yearBorn: this.yearBorn,
                weight: this.weight,
                height: this.height,
                bmi:bmi
             })
             this.fullName=''
             this.yearBorn=''
             this.weight=''
             this.height=''

            }
        }
}
</script>
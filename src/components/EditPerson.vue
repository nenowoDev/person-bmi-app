<template>
  <div>
    <h3>Edit Person</h3>

    <!-- Step 1: Input index -->
    <input
      type="number"
      v-model.number="editIndex"
      placeholder="Enter index to edit"
      @input="loadPerson"
    />

    <!-- Step 2: Feedback -->
    <div class="feedback">
      <em v-if="!validIndex">Enter an index to load person data</em>
      <em v-else>Editing: {{ person.name }} (Index {{ editIndex }})</em>
    </div>

    <!-- Step 3: Form -->
    <div v-if="validIndex" class="edit-form-section">
      <input v-model="person.name" placeholder="Name" type="text" />
      <input v-model.number="person.yob" placeholder="Year Born (YYYY)" type="number" />
      <input v-model.number="person.weight" placeholder="Weight (kg)" type="number" />
      <input v-model.number="person.height" placeholder="Height (cm)" type="number" />
      <input v-model="person.photoUrl" placeholder="Image URL" type="text" />

      <div v-if="errorMessage" class="error">{{ errorMessage }}</div>

      <button @click="updatePerson">Update</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "EditPerson",
  props: ["personList"],
  data() {
    return {
      editIndex: null,
      person: {},
      validIndex: false,
      errorMessage: "",
    };
  },
  methods: {
    loadPerson() {
      const person = this.personList?.[this.editIndex];
      if (person) {
        this.person = { ...person };
        this.validIndex = true;
        this.errorMessage = "";
      } else {
        this.validIndex = false;
        this.errorMessage = "";
      }
    },
    validate() {
      const year = new Date().getFullYear();
      if (!this.person.name.trim()) return "Name cannot be empty.";
      if (!this.person.yob || this.person.yob < 1900 || this.person.yob > year)
        return "Year Born must be between 1900 and current year.";
      if (!this.person.weight || this.person.weight <= 0) return "Weight must be positive.";
      if (!this.person.height || this.person.height <= 0) return "Height must be positive.";
      return "";
    },
    updatePerson() {
      this.errorMessage = this.validate();
      if (this.errorMessage) return;

      const heightM = this.person.height / 100;
      this.person.bmi = (this.person.weight / (heightM * heightM)).toFixed(2);
      this.person.age = new Date().getFullYear() - this.person.yob;

      this.$emit("update-person", this.editIndex, this.person);
      alert("Updated successfully.");
      this.validIndex = false;
      this.editIndex = null;
    },
  },
};
</script>

<style scoped>
.edit-form-section {
  background: #f8f8f8;
  padding: 10px;
  margin-top: 10px;
  border-radius: 6px;
}
.feedback {
  margin-top: 8px;
  font-size: 14px;
  color: #444;
}
.error {
  color: red;
  margin-top: 8px;
}
</style>

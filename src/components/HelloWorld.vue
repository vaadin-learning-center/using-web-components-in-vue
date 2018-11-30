<template>
  <div class="component">
    <div class="form" @keyup.enter="addPerson">
      <vaadin-text-field label="First Name" v-model="currentPerson.firstName"></vaadin-text-field>
      <vaadin-text-field label="Last Name" v-model="currentPerson.lastName"></vaadin-text-field>
      <vaadin-button @click="addPerson">Add</vaadin-button>
    </div>
    <vaadin-grid :items.prop="people">
      <vaadin-grid-column path="firstName" header="First name"></vaadin-grid-column>
      <vaadin-grid-column path="lastName" header="Last name"></vaadin-grid-column>
    </vaadin-grid>
  </div>
</template>

<script>
import "@vaadin/vaadin-button";
import "@vaadin/vaadin-grid";
import "@vaadin/vaadin-text-field";

const getPerson = () => {
  return {
    firstName: "",
    lastName: ""
  };
};
export default {
  name: "HelloWorld",
  data: function() {
    return {
      people: [{ firstName: "foo", lastName: "bars" }],
      currentPerson: getPerson()
    };
  },
  methods: {
    addPerson: function() {
      this.people = [...this.people, this.currentPerson];
      this.currentPerson = getPerson();
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.form {
  margin-bottom: 16px;
}
.form * {
  margin-right: 4px;
}
</style>

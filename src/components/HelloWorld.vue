<template>
  <div class="component">
    <div class="form" @keyup.enter="addPerson">
      <vaadin-text-field
        label="First Name"
        :value="currentPerson.firstName"
        @input="currentPerson.firstName = $event.target.value"
      ></vaadin-text-field>
      <vaadin-text-field
        label="Last Name"
        :value="currentPerson.lastName"
        @input="currentPerson.lastName = $event.target.value"
      ></vaadin-text-field>
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

class Person {
  constructor() {
    this.firstName = "";
    this.lastName = "";
  }
}
export default {
  name: "HelloWorld",
  data: function() {
    return {
      people: [],
      currentPerson: new Person()
    };
  },
  methods: {
    addPerson: function() {
      this.people = [...this.people, this.currentPerson];
      this.currentPerson = new Person();
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

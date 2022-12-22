<template>
  <div>
    v-for="(textField, i) in textFields"
     :key="i"
     class="text-fields-row"
    >
      <v-text-field
       :label="textField.label1"
       v-model="textField.value1"
      ></v-text-field>

      <v-text-field
       :label="textField.label2"
       v-model="textField.value2"
      ></v-text-field>

      <v-btn @click="remove(i)" class="error">delete</v-btn>
  </div>
</template>

<script>
export default {
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

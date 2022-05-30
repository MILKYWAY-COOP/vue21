<script>
export default {
  data() {
    return {
      text: 'Edit me',
      checked: true,
      checkedNames: ['Jack'],
      picked: 'One',
      selected: 'A',
      multiSelected: ['A']
    };
  }
};
</script>

<template>
  <h2>Text Input</h2>
  <input v-model="text" />{{ text }}

  <h2>CheckBox</h2>
  <input type='checkbox' id='checkbox' v-model='checked'>
  <label for='checkbox'>Checked: {{checked}}</label>


  <!-- Multiple checkboxes can bind to the same array v-model value -->
  <h2>Multi CheckBox</h2>
  <input type='checkbox' id='jack' value='Jack' v-model='checkedNames'>
  <label for='jack'>Jack</label>
  <input type='checkbox' id='john' value='John' v-model='checkedNames'>
  <label for='john'>John</label>
  <input type='checkbox' id='mike' value='Mike' v-model='checkedNames'>
  <label for='mike'>Mike</label>

</template>

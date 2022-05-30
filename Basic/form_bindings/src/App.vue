<script>
export default {
  data() {
    return {
      text: 'Edit me',
      checked: true,
      checkedNames: [],
      picked: '',
      selected: '',
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
  <input type='checkbox' id='mike' value='Add this value' v-model='checkedNames'>
  <label for='mike'>Mike</label>
  <p>Checked names: <pre>{{checkedNames}}</pre></p>

  <h2>Radio</h2>
  <input type='radio' id='one' value='one' v-model='picked'>
  <label for='one'>One</label>
  <br>
  <input type='radio' id='two' value='two' v-model='picked'>
  <label for='two'>Two</label>
  <br>
  <span>Picked: {{picked}}</span>

  <h2>Select</h2>
  <select v-model='selected'>
  <option disabled value=''>Please Select One</option>
  <option>A</option>
  <option>B</option>
  <option>C</option>
  </select>
  <br>
  <span>Selected: {{selected}}</span>

  
</template>

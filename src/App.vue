<template>
  <div id="app">
    <ul>
      <li v-for="(input, index) in inputs" :key="input.name">
        <Checkbox
            :name="input.name"
            :checked="input.checked"
            :change="handleChange(index)"
            :disabled="Boolean(input.disabled)"
        >
          {{ input.label }}
        </Checkbox>
      </li>
    </ul>
  </div>
</template>

<script>
import Checkbox from './components/Checkbox.vue'

export default {
    name: 'App',
    components: {
        Checkbox
    },
    data(){
      return {
          inputs: [{
              checked: false,
              name: 'checkbox-1',
              label: 'Checkbox'
          },{
              checked: false,
              disabled: true,
              name: 'checkbox-2',
              label: 'Checkbox Disabled'
          },]
      }
    },
    methods: {
      handleChange(index){
          return () => {
              this.inputs[index].checked = !this.inputs[index].checked
          }
      }
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

li{
  list-style: none;
  margin-bottom: 32px;
}
</style>

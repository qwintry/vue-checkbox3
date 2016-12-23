<template>
  <div>
    <vue-checkbox3 v-model="value" label="Страховка"/>
    <hr>
    <vue-checkbox3 v-model="value" :label="{ yes: 'Со страховкой', no: 'Без страховки'}"/>
    <hr>
    <vue-checkbox3 v-model="value"/>
    <hr>
    <button @click="click()">Check!</button>
  </div>
</template>
<script>
  import VueSwitch3 from './components/checkbox';

  export default {
    name: 'app',
    data() {
      return {
        value: true
      };
    },
    components: {'vue-checkbox3': VueSwitch3},
    methods: {
      click() {
        console.log(this.value);
      }
    }
  };
</script>
<style>
  body { font-family: Arial; }
</style>
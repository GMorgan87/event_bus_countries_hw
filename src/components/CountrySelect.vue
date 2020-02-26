<template lang="html">
  <div class="country-select">
    <select class="countries" v-model="selectedCountryIndex" @change="getSelectedCountry">
      <option disabled value="">Choose country</option>
      <option :value="index" v-for="(country, index) in this.countries">{{country.name}}</option>
    </select>
  </div>
</template>

<script>

import {eventBus} from '../main.js'

export default {
  name: 'country-select',
  props: ['countries'],
  data() {
    return {selectedCountryIndex: null}
  },
  methods: {
    getSelectedCountry: function() {
      eventBus.$emit('country-selected', this.selectedCountry)
    }
  },
  computed: {
    selectedCountry: function() {
      return this.countries[this.selectedCountryIndex]
    }
  }
}
</script>

<style lang="css" scoped>

  .country-select {
    margin: 0 auto;
  }

</style>

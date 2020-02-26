<template lang="html">
  <div class="country-select">
    <select class="countries" v-model="selectedCountry">
      <option disabled value="">Choose country</option>
      <option :value="index" v-for="(country, index) in this.countries">{{country.name}}</option>
    </select>
    <button @click="handleClick">View country details</button>
  </div>
</template>

<script>

import {eventBus} from '../main.js'

export default {
  name: 'country-select',
  props: ['countries'],
  data() {
    return {selectedCountry: null}
  },
  methods: {
    handleClick() {
      eventBus.$emit('country-selected', this.selectedCountry)
    }
  }
}
</script>

<style lang="css" scoped>
</style>

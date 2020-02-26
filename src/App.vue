<template>
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <country-select :countries='countries'></country-select>
      <country-details :country='selectedCountry'></country-details>
    </div>
  </div>
</template>

<script>
import CountrySelect from './components/CountrySelect.vue';
import CountryDetails from './components/CountryDetails.vue';
import {eventBus} from './main.js';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(data => this.countries = data)

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    })
  },
  components: {
    "country-select": CountrySelect,
    "country-details": CountryDetails
  }
}
</script>

<style>
  .main-container {
    justify-content: center;
  }
</style>

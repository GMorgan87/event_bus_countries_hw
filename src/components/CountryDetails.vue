<template lang="html">
  <div class="details">
    <br><br>
    <h3>{{country.name}}</h3>
    <h4>Capital: {{country.capital}}</h4>
    <h4>Population: {{country.population}}</h4>
    <h4>Languages spoken:</h4><div class="languages" v-for="language in country.languages">
      <span>{{language.name}}</span></div>
      <img :src="country.flag">
    </div>
</template>

<script>
export default {
  name: 'country-details',
  props: ['country']
}
</script>

<style lang="css" scoped>
  .details {
    height: 40%;
    width: 40%;
    opacity: 70%;
    color: black;
    text-align: center;
    margin: 10 auto;
    position: absolute;
    /* background-image: url(:src="country.flag"); */
  }

  img {
    width: 100%;
    height: 100%;
    opacity: 100%;
    /* margin-left: 50%; */
    margin-top: 30px;
    margin-left: 100px;
    transform: translate(-10%, -80%);
    position: relative;
  }

  img:hover {
    opacity: 10%;
  }

</style>

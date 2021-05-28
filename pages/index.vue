<template>
  <div class="bg-light-primary dark:bg-dark-primary">
    <Navigation />
    <Search-Filter v-model="search" :onFilter="handleFilter" />
    <Country-cards :isLoading="isLoading" :countries="countries" />
  </div>
</template>
<script>
export default {
  name: 'Home',
  data() {
    return {
      isLoading: false,
      countries: [],
      search: '',
      region: 'All',
    }
  },
  created() {
    this.loadCountries()
  },
  methods: {
    convertResultToCountry(result) {
      return result.map((entry) => ({
        image: entry.flag,
        countryName: entry.name,
        population: entry.population,
        region: entry.region,
        capital: entry.capital,
      }))
    },
    loadCountries() {
      this.isLoading = true
      fetch('https://restcountries.eu/rest/v2/all')
        .then((resp) => resp.json())
        .then((result) => {
          this.countries = this.convertResultToCountry(result)
        })
        .finally(() => {
          this.isLoading = false
        })
    },
    searchCountry() {
      this.isLoading = true

      let url = 'https://restcountries.eu/rest/v2/'

      if (this.region === 'All') {
        url += `name/${this.search}`
      } else {
        url += `region/${this.region}`
      }

      fetch(url)
        .then((response) => response.json())
        .then((result) => {
          this.countries = this.convertResultToCountry(result)
        })
        .finally(() => (this.isLoading = false))
    },
    handleFilter(region) {
      this.region = region
    },
  },
  watch: {
    search(value) {
      if (value.length > 0) this.region = 'All'

      if (value === '') {
        this.loadCountries()
      } else {
        this.searchCountry()
      }
    },
    region(value) {
      if (value === 'All') {
        this.loadCountries()
      } else {
        this.searchCountry()
      }
    },
  },
}
</script>

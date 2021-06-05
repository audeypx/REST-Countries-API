<template>
  <div>
    <Navigation />
    <nuxt-link to="/" class="back-button-wrapper">
      <button
        class="
          back-button
          bg-light-secondary
          dark:bg-dark-secondary
          text-light-text
          dark:text-dark-text
        "
      >
        <strong>Back</strong>
      </button>
    </nuxt-link>
    <p v-if="isLoading">loading...</p>
    <div v-if="isLoading">
      <div v-for="(country, index) in countries" :key="index" class="country">
        <div class="country-flag">
          <img :src="country.image" :alt="country.name" />
          pic
        </div>

        <div class="country-content">
          <div class="country-name">
            <h1>{{ country.name }}</h1>
          </div>

          <div class="country-details">
            <ul>
              <li>
                <h4 class="font-bold">
                  Native Name:
                  <span class="font-light">{{ country.nativeName }}</span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Population:
                  <span class="font-light">{{ population }}</span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Region:
                  <span class="font-light">{{ country.region }}</span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Sub Region:
                  <span class="font-light">{{ country.subregion }}d</span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Capital:
                  <span class="font-light">{{ country.capital }}</span>
                </h4>
              </li>
            </ul>
          </div>

          <div class="country-details">
            <ul>
              <li>
                <h4>
                  Top Level Domain:
                  <span class="font-light"> {{ country.topLevelDomain }}</span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Currency:
                  <span class="font-light">
                    {{ country.currencies[0].name }}(
                    {{ country.currencies[0].code }})
                  </span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Languages:
                  <span class="font-light">{{ languages }}</span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Time Zone:
                  <span class="font-light time-zone-wrapper">
                    {{ country.timezones }}
                  </span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Calling Code:
                  <span class="font-light">
                    {{ country.callingCodes }}
                  </span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Alpha Code:
                  <span class="font-light">
                    {{ country.alpha3Code }}
                    testing something
                  </span>
                </h4>
              </li>
            </ul>
          </div>

          <div class="country-details">
            <h4 class="font-bold">Border Countries</h4>

            <div class="border-country-wrapper">
              <div
                v-for="(borders, index) in borderCountries"
                :key="index"
                class="
                  border
                  bg-light-secondary
                  dark:bg-dark-secondary
                  text-light-text
                  dark:text-dark-text
                "
              >
                {{ borders }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div
      class="
        text-center
        p-4
        bg-light-secondary
        dark:bg-dark-secondary
        text-light-text
        dark:text-dark-text
      "
    >
      <code>
        Developed by
        <a
          href="https://github.com/audeypx"
          target="_blank"
          class="font-bold text-light-text dark:text-dark-text"
          >Audrey</a
        >
      </code>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Detail',
  data() {
    return {
      currentIndex: 0,
      isLoading: false,
      countries: [],
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
        nativeName: entry.nativeName,
        subregion: entry.subregion,
        topLevelDomain: entry.topLevelDomain,
        currencies: entry.currencies,
        languages: entry.languages,
        timezones: entry.timezones,
        callingCodes: entry.callingCodes,
        alpha3code: entry.alpha3code,
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
  },
}
</script>

<style scoped>
.border-country-wrapper {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
}
.border {
  font-weight: bold;
  margin: 8px 0;
  padding: 8px;
  text-align: center;
  border-radius: 5px;
  box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.2);
  transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}

.back-button-wrapper .back-button {
  display: flex;
  align-items: center;
  padding: 1em;
  box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.2);
  border-radius: 5px;
  border: none;
  cursor: pointer;
  outline: none;
}
strong {
  margin-left: 8px;
}

.country,
.country-content,
.country-details {
  margin: 24px 0;
}
.country-flag {
  width: 100%;
}
.country-flag img {
  max-width: 100%;
  height: auto;
}

.country-details ul {
  list-style: none;
}

.country-details ul li {
  margin-bottom: 8px;
}
.time-zone-wrapper {
  word-wrap: break-word;
}
</style>

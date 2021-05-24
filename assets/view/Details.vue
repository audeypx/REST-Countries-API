<template>
  <div>
    <Navigation />
    <div class="back-button-wrapper">
      <button class="back-button">
        <strong>Back</strong>
      </button>
    </div>

    <div v-if="isLoading">
      <div class="country" v-for="item in country" :key="item.name">
        <div class="country-flag">
          <img :src="item.flag" :alt="item.name" />
        </div>

        <div class="country-content">
          <div class="country-name">
            <h1>{{ item.name }}</h1>
          </div>

          <div class="country-details">
            <ul>
              <li>
                <h4 class="font-bold">
                  Native Name:
                  <span class="font-light">{{ item.nativeName }}</span>
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
                  <span class="font-light">{{ item.region }}</span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Sub Region:
                  <span class="font-light">{{ item.subregion }}</span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Capital:
                  <span class="font-light">{{ item.capital }}</span>
                </h4>
              </li>
            </ul>
          </div>

          <div class="country-details">
            <ul>
              <li>
                <h4>
                  Top Level Domain:
                  <span class="font-light">
                    {{ item.topLevelDomain }}
                  </span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Currency:
                  <span class="font-light">
                    {{ item.currencies[0].name }}(
                    {{ item.currencies[0].code }})
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
                    {{ item.timezones }}
                  </span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Calling Code:
                  <span class="font-light">
                    {{ item.callingCodes }}
                  </span>
                </h4>
              </li>

              <li>
                <h4 class="font-bold">
                  Alpha Code:
                  <span class="font-light">
                    {{ item.alpha3Code }}
                  </span>
                </h4>
              </li>
            </ul>
          </div>

          <div class="country-details">
            <h4 class="font-bold">Border Countries</h4>

            <div class="border-country-wrapper">
              <div
                class="border"
                v-for="(borders, index) in borderCountries"
                :key="index"
              >
                {{ borders }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="details">
      <code>
        Developed by
        <a href="https://github.com/audeypx" target="_blank">Audrey</a>
      </code>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>
.border-country-wrapper {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
}
.border {
  background: var(--secondary);
  color: var(--text-color);
  font-weight: bold;
  margin: 8px 0;
  padding: 8px;
  text-align: center;
  border-radius: 5px;
  box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.2);
  transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}

.details {
  text-align: center;
  background: var(--secondary);
  color: var(--text-color);
  padding: 1em;
}
a {
  color: var(--text-color);
  font-weight: bold;
}

.back-button-wrapper .back-button {
  display: flex;
  align-items: center;
  padding: 1em;
  box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.2);
  border-radius: 5px;
  background: var(--secondary);
  border: none;
  color: var(--text-color);
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

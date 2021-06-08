<template>
  <div class="my-12 mx-auto px-4 md:px-12">
    <p v-if="isLoading">loading...</p>
    <div v-else class="card-container">
      <nuxt-link
        v-for="(country, index) in countries"
        :key="index"
        to="/details"
        class="
          card
          rounded-lg
          my-8
          cursor-pointer
          bg-light-secondary
          dark:bg-dark-secondary
          text-light-text
          dark:text-dark-text
        "
      >
        <div class="card-image">
          <img
            class="block w-full h-52"
            :src="country.image"
            alt="card-image"
          />
        </div>
        <div class="card_content py-4 px-8">
          <div class="card_content-title pb-8">
            <h2 class="font-bold text-3xl">{{ country.countryName }}</h2>
          </div>
          <div class="card_content-info">
            <h4 class="font-bold pb-4">
              Population :
              <span class="font-light">{{ country.population }}</span>
            </h4>
            <h4 class="font-bold pb-4">
              Region :
              <span class="font-light">{{ country.region }}</span>
            </h4>
            <h4 class="font-bold pb-4">
              Capital:
              <span class="font-light">{{ country.capital }}</span>
            </h4>
          </div>
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CountryCards',
  props: {
    countries: {
      type: Array,
      default: () => [],
    },
    isLoading: {
      type: Boolean,
    },
  },

  data() {
    return {
      currentIndex: 0,
    }
  },
}
</script>

<style scoped>
.card-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 2em;

  /* padding: 0 4em; */
  box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.2);
  transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}
.card:hover {
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
}

@media (max-width: 900px) {
  .card-container {
    grid-template-columns: repeat(2, 1fr);
    padding: 16px;
  }
}

@media (max-width: 768px) {
  .card-container {
    grid-template-columns: 100%;
    padding: 16px;
  }
}

img {
  width: 100%;
  height: 180px;
  object-fit: cover;
  border-radius: 5px 5px 0 0;
}

.card .card_content {
  transform: scale(0.9);
}

.card .card_content .card_content-info h4 {
  line-height: 30px;
}
</style>

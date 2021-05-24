<template>
  <div class="my-12 mx-auto px-4 md:px-12">
    <div class="card-container">
      <div
        class="
          card
          rounded-lg
          my-8
          cursor-pointer
          bg-light-secondary
          text-light-text
        "
        v-for="(card, index) in cards"
        :key="index"
      >
        <div class="card-image">
          <img class="block w-full h-52" :src="card.image" alt="card-image" />
        </div>
        <div class="card_content py-4 px-8">
          <div class="card_content-title pb-8">
            <h2 class="font-bold text-3xl">{{ card.countryName }}</h2>
          </div>
          <div class="card_content-info">
            <h4 class="font-bold pb-4">
              Population :
              <span class="font-light">{{ card.population }}</span>
            </h4>
            <h4 class="font-bold pb-4">
              Region :
              <span class="font-light">{{ card.region }}</span>
            </h4>
            <h4 class="font-bold pb-4">
              Capital:
              <span class="font-light">{{ card.capital }}</span>
            </h4>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CountryCards',
  props: ['image', 'countryName', 'population', 'region', 'capital'],
  data() {
    return {
      currentIndex: 0,
      cards: [
        {
          image: 'https://picsum.photos/600/400/?random',
          countryName: 'Nigeria',
          population: '13,0000',
          region: 'Africa',
          capital: 'Abuja',
        },
        {
          image: 'https://picsum.photos/600/400/?random',
          countryName: 'Nigeria',
          population: '13,0000',
          region: 'Africa',
          capital: 'Abuja',
        },
        {
          image: 'https://picsum.photos/600/400/?random',
          countryName: 'Nigeria',
          population: '13,0000',
          region: 'Africa',
          capital: 'Abuja',
        },
        {
          image: 'https://picsum.photos/600/400/?random',
          countryName: 'Nigeria',
          population: '13,0000',
          region: 'Africa',
          capital: 'Abuja',
        },
        {
          image: 'https://picsum.photos/600/400/?random',
          countryName: 'Nigeria',
          population: '13,0000',
          region: 'Africa',
          capital: 'Abuja',
        },
        {
          image: 'https://picsum.photos/600/400/?random',
          countryName: 'Nigeria',
          population: '13,0000',
          region: 'Africa',
          capital: 'Abuja',
        },
        {
          image: 'https://picsum.photos/600/400/?random',
          countryName: 'Nigeria',
          population: '13,0000',
          region: 'Africa',
          capital: 'Abuja',
        },
        {
          image: 'https://picsum.photos/600/400/?random',
          countryName: 'Nigeria',
          population: '13,0000',
          region: 'Africa',
          capital: 'Abuja',
        },
        {
          image: 'https://picsum.photos/600/400/?random',
          countryName: 'Nigeria',
          population: '13,0000',
          region: 'Africa',
          capital: 'Abuja',
        },
        {
          image: 'https://picsum.photos/600/400/?random',
          countryName: 'Nigeria',
          population: '13,0000',
          region: 'Africa',
          capital: 'Abuja',
        },
      ],
    }
  },
}
</script>

<style scoped>
.card-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 60px;

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
  height: 100%;
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

<template>
  <main class="">
    <div class="action-bar lg:flex items-center lg:justify-between p-8">
      <div
        class="
          search-wrapper
          w-full
          md:w-2/6
          flex
          items-center
          bg-light-secondary
          relative
        "
      >
        <input
          type="text"
          aria-label="Search Field"
          placeholder="Search for a country..."
        />
      </div>

      <!-- <p>
        <strong class="search-err">{{ search_error_message }}</strong>
      </p> -->

      <div class="filter-wrapper mt-4 w-3/5 md:w-1/5">
        <button
          class="
            filter-btn
            flex
            justify-between
            cursor-pointer
            bg-light-secondary
            text-light-text
            border-none
            p-4
            items-center
            w-full
            outline-none
            menu-toggle
          "
          @click="showDropDown = !showDropDown"
        >
          <strong>Filter By Region</strong>
          <svg
            v-if="!showDropDown"
            xmlns="http://www.w3.org/2000/svg"
            class="icon icon-tabler icon-tabler-chevron-down"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            stroke-width="2"
            stroke="#000000"
            fill="none"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path stroke="none" d="M0 0h24v24H0z" fill="none" />
            <polyline points="6 9 12 15 18 9" />
          </svg>

          <svg
            v-else
            xmlns="http://www.w3.org/2000/svg"
            class="icon icon-tabler icon-tabler-chevron-up"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            stroke-width="2"
            stroke="#000000"
            fill="none"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path stroke="none" d="M0 0h24v24H0z" fill="none" />
            <polyline points="6 15 12 9 18 15" />
          </svg>
        </button>

        <transition name="slide">
          <ul v-if="showDropDown" class="filter-content list-none">
            <li class="" @click="filter('Africa')">Africa</li>
            <li @click="filter('Americas')">Americas</li>
            <li @click="filter('Americas')">Americas</li>
            <li @click="filter('Asia')">Asia</li>
            <li @click="filter('Europe')">Europe</li>
            <li @click="filter('Oceania')">Oceania</li>
          </ul>
        </transition>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'filter',
  data() {
    return {
      showDropDown: false,
    }
  },
}
</script>
<style scoped>
*:focus {
  outline: none;
}

main .action-bar .search-wrapper {
  box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.2);
  border-radius: 5px;

  /* width: 30%; */
}

main .action-bar .search-wrapper input {
  border: none;
  padding: 1.2em;
  width: 100%;
  margin-left: 8px;
  background: transparent;
  outline: none;
  color: theme('colors.light.text');
}

/* main .action-bar .filter-wrapper {
  width: 20%;
} */

main .action-bar .filter-wrapper select {
  appearance: none;
  padding: 1.2em;
  border: none;
  width: 60%;
  outline: none;
  box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.2);
  background: theme('colors.light.primary');
  border-radius: 5px;
}

main .action-bar .filter-wrapper .filter-btn {
  box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.2);
  border-radius: 5px;
}

.filter-content {
  background: theme('colors.light.secondary');
  box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.2);
  padding: 16px;
  margin: 2% auto;
  border-radius: 5px;
  z-index: 9999;
  width: inherit;
  position: absolute;
  transform-origin: top;
  transition: transform 0.4s ease-in-out;
  overflow: hidden;

  --tw-bg-opacity: 0.9;

  color: theme('colors.light.text');
}

.filter-content li {
  padding: 0.5rem;
  cursor: pointer;
}

.filter-content li:hover {
  font-weight: bold;
}

.slide-enter,
.slide-leave-to {
  transform: scaleY(0);
}
</style>

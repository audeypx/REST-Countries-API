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
          dark:bg-dark-secondary
          relative
        "
      >
        <input
          type="text"
          aria-label="Search Field"
          placeholder="Search for a country..."
          @input="handleInput"
          class="text-light-text dark:text-dark-text"
        />
      </div>

      <div class="filter-wrapper mt-4 w-3/5 md:w-1/5">
        <button
          class="
            filter-btn
            flex
            justify-between
            cursor-pointer
            bg-light-secondary
            dark:bg-dark-secondary
            text-light-text
            dark:text-dark-text
            border-none
            p-4
            items-center
            w-full
            outline-none
            menu-toggle
          "
          @click="showDropDown = !showDropDown"
        >
          <strong>{{ filterText }}</strong>
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
          <ul
            v-if="showDropDown"
            class="
              filter-content
              list-none
              bg-light-secondary
              dark:bg-dark-secondary
            "
          >
            <li
              class="text-light-text dark:text-dark-text"
              @click="handleFilter('All')"
            >
              All
            </li>
            <li
              class="text-light-text dark:text-dark-text"
              @click="handleFilter('Africa')"
            >
              Africa
            </li>
            <li
              class="text-light-text dark:text-dark-text"
              @click="handleFilter('Americas')"
            >
              Americas
            </li>
            <li
              class="text-light-text dark:text-dark-text"
              @click="handleFilter('Asia')"
            >
              Asia
            </li>
            <li
              class="text-light-text dark:text-dark-text"
              @click="handleFilter('Europe')"
            >
              Europe
            </li>
            <li
              class="text-light-text dark:text-dark-text"
              @click="handleFilter('Oceania')"
            >
              Oceania
            </li>
          </ul>
        </transition>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'filter',
  props: {
    value: {},
    onFilter: {
      type: Function,
      default: () => ({}),
    },
  },
  data() {
    return {
      showDropDown: false,
      search: this.value,
      filterText: 'Filter By Region',
    }
  },
  methods: {
    handleInput(event) {
      this.$emit('input', event.target.value)
    },
    handleFilter(value) {
      this.filterText = value
      this.onFilter(value)
      this.showDropDown = false
    },
  },
  watch: {
    value(value) {
      if (value !== '') {
        this.filterText = 'All'
      }
    },
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

  /* background: theme('colors.light.primary'); */
  border-radius: 5px;
}

main .action-bar .filter-wrapper .filter-btn {
  box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.2);
  border-radius: 5px;
}

.filter-content {
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

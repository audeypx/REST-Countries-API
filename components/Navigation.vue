<template>
  <nav
    class="
      flex
      justify-between
      items-center
      relative
      p-6
      md:py-8
      md:px-16
      bg-light-primary
      dark:bg-dark-primary
    "
  >
    <div class="header-text">
      <h3 class="font-extrabold text-light-text dark:text-dark-text">
        Where in the world?
      </h3>
    </div>
    <div class="toggle-btn flex items-center cursor-pointer">
      <label class="switch relative inline-block">
        <!-- <p>{{ toggle ? toDark() : toLight() }}</p> -->
        <input type="checkbox" @click="toDark" />
        <span class="slider round"></span>
      </label>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Toggle',
  data() {
    return {
      toggle: false,
      showSkeleton: true,
    }
  },

  methods: {
    toDark() {
      const theme = localStorage.getItem('theme')
      if (!theme) {
        localStorage.setItem('theme', 'dark')
      }
      if (theme !== 'dark') {
        localStorage.setItem('theme', 'dark')
        document.documentElement.classList.add('dark')
      } else {
        localStorage.setItem('theme', 'light')
        document.documentElement.classList.remove('dark')
      }
    },
  },
}
</script>

<style scoped>
.switch {
  width: 60px;
  height: 34px;
  margin-left: 8px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider::before {
  position: absolute;
  content: '';
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: #2196f3;
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196f3;
}

input:checked + .slider::before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

.slider.round {
  border-radius: 34px;
}

.slider.round::before {
  border-radius: 50%;
}

nav {
  z-index: 9999;
  box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.2);
}
</style>

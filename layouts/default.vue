<template>
  <div>
    <Nuxt />
  </div>
</template>

<style>
/* Default variable colours */
:root {
  --primary: hsl(0, 0%, 98%);
  --secondary: hsl(0, 0%, 100%);
  --text-color: hsl(200, 15%, 8%);
}

[data-theme='dark'] {
  --primary: hsl(207, 26%, 17%);
  --secondary: hsl(209, 23%, 22%);
  --text-color: hsl(0, 0%, 100%);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-family: 'Nunito Sans', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: theme('colors.light.primary');
}
</style>

<template>
  <div class="container">
    <appHeader/>
    <nuxt />
  </div>
</template>

<script>
import appHeader from "../components/appHeader";
export default {
  components: {
    appHeader
  },
  name: "default",
}


</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Mulish:wght@400;900&family=Roboto+Slab:wght@400;900&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Mulish', sans-serif;
  color: #333333;
}

.dark-mode body {
  background: #333333;
}

.dark-mode * {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Roboto Slab', sans-serif;
  color: #e3e3e3;
}

.container {
  max-width: 90%;
  margin: 2rem auto;
  overflow: hidden;
  padding: 1rem 2rem;
}

.dark-mode .container {
  max-width: 90%;
  margin: 2rem auto;
  overflow: hidden;
  padding: 1rem 2rem;
}

ul {
  list-style: none;
}
</style>

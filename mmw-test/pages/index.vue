<template>
  <div>
    <Home />
  </div>
</template>

<script>
import Home from "../components/Home";
export default {
  components: {Home},

  methods:{

  },
}
</script>
<style>
.dark-mode body {
  background: url("../Images/dark_background.jpg") no-repeat fixed center;
}

body {
  background: url("../Images/blue_background.jpg") no-repeat fixed center;
}
</style>

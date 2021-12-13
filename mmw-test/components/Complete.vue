<template>
  <div>
    <div class="container">
      <h1>Thank You<br> For Your Enquiry!</h1>
      <h2>We will be in touch with you soon</h2>
      <nuxt-link to="/">
        <button class="return">Return To Start</button>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "Complete",
}
</script>

<style scoped>

.container {
  justify-content: center;
  align-items: center;
  text-align: center;
  margin-bottom: 0;
  margin-top: 2rem;
}

h1 {
  font-weight: 900;
  margin-bottom: 2rem;
  font-size: 4rem;
}

h2 {
  font-weight: 400;
  margin-bottom: 2rem;
  font-size: 2.5rem;
}

.return {
  padding: 1.2rem 3rem;
  background: #20c763;
  color: #ffffff;
  font-weight: 900;
  font-size: 2rem;
  border: none;
}

.dark-mode .return{
  background: #fdd842;
  color: #333333;
  border-radius: 50px;
}
</style>


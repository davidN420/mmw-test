<template>
  <div>
    <div class="container">
      <h1>Mainline Menswear<br>Frontend Technical Test</h1>
      <h3>Product Enquiry Web Application</h3>
      <nuxt-link to="/items">
        <button class="start">START</button>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
}
</script>

<style scoped>

  .container {
    justify-content: center;
    align-items: center;
    text-align: center;
    margin-bottom: 0;
    margin-top: 2rem;
    background: transparent;
  }

  h1 {
    font-weight: 900;
    margin-bottom: 2rem;
    font-size: 4rem;
  }

  h3 {
    font-weight: 400;
    margin-bottom: 2rem;
    font-size: 2.5rem;
  }

  .start{
    padding: 1.2rem 6rem;
    background: #20c763;
    color: white;
    font-weight: 900;
    font-size: 2rem;
    border: none;
  }

  .dark-mode .start {
    padding: 1.2rem 6rem;
    background: #fdd842;
    color: #333333;
    font-weight: 900;
    font-size: 2rem;
    border: none;
    border-radius: 50px;
  }
</style>

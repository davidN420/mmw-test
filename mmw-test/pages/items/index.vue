<template>
  <div class="page">
    <h2 class="title">Product Enquiry Web Application</h2>
    <div class="items">
      <Items v-for="item in items" :key="item.product_id"
             :product_id="item.product_id" :name="item.name"
             :exclusive="item.exclusive" :rrp_price="item.rrp_price"
             :sale_price="item.sale_price"/>
    </div>
  </div>
</template>

<script>
import Items from "../../components/Items";
export default {
  name: "items",
  head(){
    return{
      title: 'Product Enquiry Web Application',
    }
  },

  components: {Items},

  data() {
    return {
      items: []
  }
  },
  async fetch() {
    this.items = await fetch(
      'https://frontendtest.mainlinemenswear.co.uk/products'
    ).then(res => res.json())
    console.log(this.items)
  },

  async bastard(){

    for(let item in this.Items) {
      if (item.exclusive === '1') {
        console.log();
      }
    }
  }
}
</script>

<style scoped>
  body {
    background: #ffffff none;
  }
  .dark-mode body {
    background: #616161 none;
  }
  .page {
    background: #107cbb linear-gradient(to right, #107cbb, #64c1f7);
  }

  .dark-mode .page {
    background: #333333 linear-gradient(to top right, #333333, #616161);
  }

  .title{
    color: #333333;
    font-weight: 400;
    position: absolute;
    top: 4rem;
    left: 40rem;
  }

  .dark-mode .title {
    color: #e3e3e3;
  }

 .items{
   display: flex;
   justify-content: center;
 }
</style>

<template>
  <div class="item">
    <div v-if="exclusive != 0" class="exclusive">EXCLUSIVE</div>
    <div>
      <img class="item-image" :src="require(`../Images/${product_id}.jpg`)" width="200" height="200">
    </div>
    <h3 class="name">{{name}}</h3>
    <p v-show="sale_price == 0"class="rrp-price">£{{rrp_price}}.00</p>
    <p v-show="sale_price != 0"class="rrp-price-strike">£{{rrp_price}}.00</p>
    <p v-show="sale_price != 0" class="sale-price">SALE £{{sale_price}}.00</p>
  </div>

</template>

<script>

export default {
  name: "Product",
  props: ['product_id', 'name',
    'rrp_price','sale_price', 'exclusive'],

}
</script>

<style scoped>

.item {
  max-width: 16rem;
  max-height: 80rem;
  align-items: center;
  margin: 0.8rem;
  padding: 2rem 1rem;
  justify-content: center;
  text-align: center;
}

.name{
  font-size: 1rem;
  margin: 0;
  font-weight: 400;
}
.exclusive{
  background: #d0eeff;
  padding: .2rem;
  margin-bottom: 0.4rem;
}

.dark-mode .exclusive{
  background: #107cbb;
}

.item-image{
  border: solid 1px #e3e3e3;
}

.dark-mode .item-image{
  border: solid 1px #333333;
}

.rrp-price{
  font-weight: 900;
  font-size: 1.6rem;
  margin-top: 2rem;
}

.rrp-price-strike {
  text-decoration: line-through;
  font-size: 0.8rem;
  color: #333333;
}

.dark-mode .rrp-price-strike{
  color: #e3e3e3;
}

.sale-price {
  color: red;
  font-weight: 900;
  font-size: 1.6rem;
}
</style>


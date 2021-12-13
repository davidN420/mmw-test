<template>
  <div class="item">
    <div v-show="exclusive != 0" class="exclusive">EXCLUSIVE</div>
    <div>
      <img class="item-image" :src="require(`../Images/${product_id}.jpg`)" width="200" height="200">
    </div>
    <h3 class="name">{{name}}</h3>
    <div class="prices">
      <p v-show="sale_price != 0"class="rrp-price-strike">£{{rrp_price}}.00</p>
      <p v-show="sale_price != 0" class="sale-price">SALE £{{sale_price}}.00</p>
      <p v-show="sale_price == 0"class="rrp-price">£{{rrp_price}}.00</p>
    </div>
    <nuxt-link :to="'items/' + product_id">
      <button class="enquire">ENQUIRE ABOUT THIS ITEM</button>
    </nuxt-link>
  </div>

</template>

<script>

export default {
  name: "Items",
  props: ['product_id', 'name',
    'rrp_price','sale_price', 'exclusive']
}
</script>

<style>

.item {
  max-width: 18rem;
  align-items: center;
  margin: 2rem;
  padding: 0.8rem 1rem;
  justify-content: center;
  text-align: center;
  background: white;
}

.dark-mode .item {
  background: #616161;
}

.name{
  font-size: 1rem;
  margin: 0;
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
  margin: 0;
  padding: 0;
}

.dark-mode .item-image{
  border: solid 1px #333333;
}

.prices{
  height: 4rem;
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

.enquire {
  padding: 1rem 1.2rem;
  margin-top: 2rem;
  margin-left: 1rem;
  margin-right: 1rem;
  background: #20c763;
  color: white;
  font-weight: 900;
  font-size: .8rem;
  border: none;
}

.dark-mode .enquire {
  background: #fdd842;
  color: #333333;
  border-radius: 50px;
}
</style>

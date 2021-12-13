<template>
  <div class="bg">
    <div v-if="isSubmitted === false" class="container">
      <h2 class="title">{{itemName}} Enquiry</h2>
      <div class="product">
        <Product v-for="item in item.product" :key="item.product_id"
                 :product_id="item.product_id" :name="item.name"
                 :exclusive="item.exclusive" :rrp_price="item.rrp_price"
                 :sale_price="item.sale_price"/>
      </div>
      <div class="size-select">
        <h3 class="size-header">SELECT YOUR SIZE*</h3>
        <select form="enqForm" v-model="formSize" name="sizes" id="sizes" required>
          <option disabled hidden :value="null">PLEASE SELECT</option>
          <option v-for="size in item.sizes" :key="size.size"
                  :value="size.size">{{size.size}}</option>
        </select>
      </div>
      <div class="form">
        <form id="enqForm" @submit="submitForm">
          <label for="fullname">Full Name*</label><br>
          <input v-model="fullName" type="text" id="fullname" name="fullname" required><br>

          <label for="email">Email*</label><br>
          <input v-model="formEmail" type="email" id="email" name="email" required><br>

          <label>Have you found this item cheaper on a competitor website?*</label><br>
          <div class="radbut">
            <label class="radio">Yes
              <input v-on:change="competitorYes" type="radio" id="Yes" name="competitor" value="Yes" required>
              <span class="checkmark"></span>
            </label>
            <label class="radio">No
              <input v-on:change="competitorNo" type="radio" id="No" name="competitor" value="No">
              <span class="checkmark"></span>
            </label>
          </div>
          <label v-if="competitor === 'Yes'" for="competitorURL">Competitor URL*</label><br>
          <input v-model="competitorURL" v-if="competitor === 'Yes'" type="text"
                 id="competitorURL" name="competitorURL" required> <br>

          <label for="Enquiry">Enquiry Message*</label>
          <label>(<span>{{chartotal}}</span>/200)</label><br>
          <textarea v-model="formEnquiry" v-on:keyup="charCount" id="Enquiry" name="Enquiry" maxlength="200" required/><br>

          <label class="asterisk">Fields marked with an asterisk* are compulsory</label>
          <input type="submit" value="SUBMIT YOUR ENQUIRY">
        </form>
      </div>
    </div>

    <div v-else class="container">
      <h2 class="title">Summary Of Your Enquiry</h2>
      <div class="product">
        <Product v-for="item in item.product" :key="item.product_id"
                 :product_id="item.product_id" :name="item.name"
                 :exclusive="item.exclusive" :rrp_price="item.rrp_price"
                 :sale_price="item.sale_price"/>
      </div>
      <div class="enquirySub">
        <p>Full Name: <span class="formResult">{{fullName}}</span></p><br>
        <p>Email: <span class="formResult">{{formEmail}}</span></p><br>
        <p>Size: <span class="formResultBold">{{formSize}}</span></p><br>
        <p>Have you found this item cheaper on a competitor website? <span class="formResultBold">{{competitor}}</span></p><br>
        <p v-if="competitor === 'Yes'">Competitor URL: <span class="formResult">{{competitorURL}}</span></p><br>
        <p>Enquiry Message:<br>" <span class="formResult">{{formEnquiry}} "</span></p>
        <div class="finish">
          <nuxt-link :to="'/items/'+ $route.params.product_id + '/enquiry'">
            <button class="finishbutton" v-on:click="enquiryPost">Finish</button>
          </nuxt-link>
        </div>
      </div>

    </div>
  </div>


</template>

<script>
import Product from "../../../components/Product";
import axios from "axios";
export default {
  name: "index",
  components: {Product},

  head(){
    return {
      title: this.itemName,
    }
  },

  data() {
    return {
      item: {},
      itemName: '',
      chartotal: 0,
      competitor: '',
      formEnquiry: '',
      fullName: '',
      formSize: null,
      formEmail: '',
      competitorURL: '',
      isSubmitted: false,
      formData: {
        productID: null,
        sizeSelected: null,
        fullname: null,
        email: null,
        competitor: null,
        competitorUrl: null,
        enquiry: null
      }
    }
  },

  async fetch() {
    this.item = await fetch(`https://frontendtest.mainlinemenswear.co.uk/product/${this.$route.params.product_id}`
    ).then(res => res.json())

    this.itemName = this.item.product[0].name;
  },

  methods: {
    charCount:function () {
      this.chartotal = this.formEnquiry.length;
    },

    competitorYes:function() {
      if(this.competitor !== 'Yes'){
        this.competitor = 'Yes';
      }
    },

    competitorNo:function() {
      if(this.competitor !== 'No') {
        this.competitor = 'No';
      }
    },

    submitForm:function() {
      this.isSubmitted = true;
    },

    /*async enquiryPost() {
      this.formData = {productId: this.$route.params.product_id, sizeSelected: this.formSize,
        fullname: this.fullName, email: this.formEmail, competitor: this.competitor,
        competitorUrl: this.competitorURL, enquiry: this.formEnquiry}

      const init = this.formData

      const data = await axios.post('https://frontendtest.mainlinemenswear.co.uk/submit', init,
        {headers:{"Content-Type" : "application/json"}}).then((res) => {
        console.log(res)
      })
    }*/
  }
}
</script>

<style scoped>
.bg {
  background: #107cbb linear-gradient(to right, #107cbb, #64c1f7);
  padding: 2rem;
}

.dark-mode .bg{
  background: #333333 linear-gradient(to top right, #333333, #616161);
}

.title{
  font-weight: 400;
  position: absolute;
  top: 4rem;
  left: 35rem;
}
.container {
  display: flex;
  background: white;
  padding: .2rem;
}

.dark-mode .container {
  background: #616161;
  border: solid #333333 1px;
}

.product {
  border-right: solid #e3e3e3 1px;
  font-weight: 400;
}

.dark-mode .product {
  border-right: solid #333333 1px;
}

.size-select {
  width: 12rem;
  padding: 2rem 0rem;
  border-right: solid #e3e3e3 1px;
  margin: 0rem 1.5rem;
  justify-items: center;
}

.dark-mode .size-select{
  border-right: solid #333333 1px;
}

.form {
  padding: 2rem 1rem;
}

#Enquiry {
  box-sizing: content-box;
  border-right: 1px;
  width: 25rem;
  height: 6rem;
  margin: .25rem 0;
  border-style: solid;
  padding: 0.2rem;
}

.dark-mode #Enquiry {
  background: #616161;
  border: solid 1.5px #e3e3e3;
}

.size-header{
  padding: 0;
  font-size: 1rem;
  font-weight: 900;
  margin-bottom: 1rem;
}

input[type="text"]{
  width: 25rem;
  height: 2rem;
  padding: 0.2rem;
  margin-bottom: 0.8rem;
}

.dark-mode input[type="text"]{
  background: #616161;
  border: solid 1.5px #e3e3e3;
}

input[type="text"]:required:invalid{
  border: solid 1.5px #ff5050;
}

input[type="email"]{
  width: 25rem;
  height: 2rem;
  padding: 0.2rem;
  margin-bottom: 0.8rem;
}

.dark-mode input[type="email"]{
  background: #616161;
  border: solid 1.5px #e3e3e3;
}

label {
  font-size: 0.8rem;
}

.asterisk {
  font-size: 0.65rem;
}

input[type="submit"]{
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

.dark-mode input[type="submit"]{
  background: #fdd842;
  color: #333333;
  border-radius: 50px;
}

.enquirySub {
  padding: 2rem 1rem;
  width: 90rem;
}

/* Customize the label (the container) */
.radio {
  display: block;
  position: relative;
  padding-left: 35px;
  margin-right: 1rem;
  margin-top: 0.5rem;
  margin-bottom: 12px;
  cursor: pointer;
  font-size: 22px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default radio button */
.radio input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom radio button */
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 25px;
  width: 25px;
  background-color: #fff;
  border-radius: 50%;
  border: #e3e3e3 solid 1.5px;
}

.dark-mode .checkmark {
  background: #616161;
}

/* On mouse-over, add a grey background color */
.radio:hover input ~ .checkmark {
  background-color: #ccc;
}

/* When the radio button is checked*/
.radio input:checked ~ .checkmark {
  background-color: #ffffff;
  border: #20c763 solid 3px;
}

.dark-mode .radio input:checked ~ .checkmark {
  background-color: #616161;
  border: #fdd842 solid 3px;
}

/* Create the indicator */
.checkmark:after {
  content: "";
  position: relative;
  display: none;
}

/* Show the indicator (dot/circle) when checked */
.radio input:checked ~ .checkmark:after {
  display: block;
}

/* Style the indicator (dot/circle) */
.radio .checkmark:after {
  left: 0.16rem;
  top: 0.12rem;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: #20c763;
}

.dark-mode .radio .checkmark:after {
  background: #fdd842;
}


.radbut {
  display: flex
}
#sizes {
  padding: .6rem 1.8rem;
  text-align: center;
  position: relative;
  right: .6rem;
}

.dark-mode #sizes {
  background: #616161;
  border: 1.5px solid #e3e3e3;
}

.formResult{
  font-style: italic;
}

.formResultBold{
  font-style: italic;
  font-weight: 900;
}
.finish{
  margin-top: 5rem;
  float: right;
}

.finishbutton {
  padding: 1rem 5rem;
  margin-top: 2rem;
  margin-left: 1rem;
  margin-right: 1rem;
  background: #20c763;
  color: white;
  font-weight: 900;
  font-size: 1rem;
  border: none;
}

.dark-mode .finishbutton{
  background: #fdd842;
  color: #333333;
  border-radius: 50px;
}
</style>

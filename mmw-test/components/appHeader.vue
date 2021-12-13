<template>
  <header class="header">
    <ul>
      <li>
        <div class="icon">
          <div v-show="active == 0" class="theme"></div>
          <fa class="fas" :icon="['fas','sun']" v-on:click="themeClickLight"/>
        </div>
      </li>
      <li>
        <div class="icon">
          <div v-show="active == 1" class="theme"></div>
          <fa class="fas" :icon="['fas','moon']" v-on:click="themeClickDark"/>
        </div>
      </li>
    </ul>
  </header>
</template>

<script>


export default {
  name: "appHeader",

  data(){
    return {
      text: {},
      active: '0'
    }
  },

  /*mounted() {
    if(this.$colorMode.preference == 'light'){
      console.log(this.$colorMode.preference)
      console.log(this.$colorMode.value)
      this.active = 1
    }else{
      this.active = 0
    }
  },*/

  methods: {
    themeClickDark(){
      this.active = 1;
      this.$colorMode.preference = 'dark';
    },

    themeClickLight(){
      this.active = 0;
      this.$colorMode.preference = 'light';
    }
  }

}
</script>

<style>
  .header {
    display: flex;
    justify-content: left;
    align-items: center;
    padding-bottom: 1rem;
  }

  .dark-mode .header {
    background: #333333 linear-gradient(to top right, #333333, #616161);
  }

  .header ul {
    display: flex;
  }

  .fas {
    display: inline-block;
    color: #333333;
    margin: 0.4rem;
    font-size: 3rem;
  }

  .dark-mode .fas {
    display: inline-block;
    margin: 0.4rem;
    font-size: 3rem;
  }{}

  .theme {
    background: #20c763;
    width: 0.75rem;
    height: 0.75rem;
    border-radius: 50%;
  }

  .dark-mode .theme {
    background: #fdd842;
    width: 0.75rem;
    height: 0.75rem;
    border-radius: 50%;
  }
</style>

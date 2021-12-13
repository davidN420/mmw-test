<template>
  <div>
    <Complete />
  </div>
</template>

<script>

import Complete from "@/components/Complete";

export default {
  name: "index",

  head(){
    return {
      title: 'Enquiry Submitted',
    }
  },

  components: {Complete},

}
</script>

<style scoped>
.dark-mode body {
  background: url("../../../../Images/dark_background.jpg") no-repeat fixed center;
}

body {
  background: url("../../../../Images/blue_background.jpg") no-repeat fixed center;
}

</style>

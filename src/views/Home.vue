<template>
  <div class="main-container">
    <h1 class="heading">The Golden Crust Bakery</h1>
    <inventory />
    
  </div>
</template>

<script>
// @ is an alias to /src
import Inventory from '../components/Inventory.vue'

export default {
  name: 'Home',
  components: {
    Inventory

  }
}
</script>

<style lang="scss" scoped>
.main-container {
  display: grid;
  place-items: center;

  .heading 
  {
    font-size: 55px;
    color: #BF3636;
  }
}

</style>

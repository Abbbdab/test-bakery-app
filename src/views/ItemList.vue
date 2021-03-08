<template>
  <div class="container">
    <h1 class="heading">Inventory</h1>
    <newItem />
    
   </div>
</template>

<script>

import newItem from '../components/AddItem.vue'

export default {
  name : 'ItemList',
  components : {
    newItem
  }
}
</script>

<style lang="scss" scoped>

.container {
  display: grid;
  place-items: center;

  h1 {
    color: #BF3636;
  }
}

</style>


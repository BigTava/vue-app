<template>
  <navbar :cart="cart" />
  <div class="container">
    <router-view :cart="cart" :products="products" @addToCart="addToCart" />
  </div>
</template>

<script>
import Navbar from '@/components/NavbarDefault'
export default {
  data: function () {
    return {
      cart: [],
      products: []
    }
  },
  components: {
    Navbar
  },
  methods: {
    addToCart(product) {
      this.cart.push(product)
      if (this.cartTotal >= 100) {
        this.salesBtn = 'btn-danger'
      }
    }
  },
  created() {
    fetch('https://hplussport.com/api/products/order/price')
      .then(response => response.json())
      .then(data => {
        this.products = data
      })
  }
}
</script>
<style lang="scss">
$primary: #6f42c1;
@import 'node_modules/bootstrap/scss/bootstrap';

.products-enter-active,
.products-leave-active {
  transition: all 0.5s ease-in-out;
}

.products-enter-from {
  opacity: 0;
  transform: translateX(300px);
}

.products-leave-to {
  opacity: 0;
  transform: translateX(-300px);
}
</style>

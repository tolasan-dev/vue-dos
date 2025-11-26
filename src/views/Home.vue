<template>
  <div>
    <div class="d-flex justify-content-between align-items-center mb-4">
      <h1 class="h3 mb-0">Products</h1>
      <div>
        <button class="btn btn-outline-secondary me-2" @click="shuffle">Shuffle</button>
        <span class="badge bg-success">Cart: {{ cart.length }}</span>
      </div>
    </div>

    <div class="row g-3">
      <div class="col-12 col-sm-6 col-md-4 col-lg-3" v-for="product in products" :key="product.id">
        <ProductCard :product="product" @add-to-cart="addToCart" />
      </div>
    </div>

    <div v-if="cart.length" class="mt-4">
      <h5>Cart items</h5>
      <ul class="list-group">
        <li class="list-group-item d-flex justify-content-between align-items-center" v-for="(p, idx) in cart" :key="idx">
          {{ p.name }}
          <span class="text-muted">${{ Number(p.price).toFixed(2) }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import ProductCard from '../components/ProductCard.vue';

export default {
  name: 'Home',
  components: { ProductCard },
  data() {
    return {
      products: [
        { id: 1, name: 'Laptop', price: 899, description: 'Powerful notebook', image: 'https://picsum.photos/seed/laptop/400/300' },
        { id: 2, name: 'Headphones', price: 199, description: 'Noise-cancelling', image: 'https://picsum.photos/seed/headphones/400/300' },
        { id: 3, name: 'Keyboard', price: 99, description: 'Mechanical keyboard', image: 'https://picsum.photos/seed/keyboard/400/300' },
        { id: 4, name: 'Monitor', price: 299, description: '24" FHD monitor', image: 'https://picsum.photos/seed/monitor/400/300' },
        { id: 5, name: 'Mouse', price: 49, description: 'Wireless mouse', image: 'https://picsum.photos/seed/mouse/400/300' },
        { id: 6, name: 'Webcam', price: 69, description: '1080p webcam', image: 'https://picsum.photos/seed/webcam/400/300' }
      ],
      cart: []
    };
  },
  methods: {
    addToCart(product) {
      this.cart.push(product);
    },
    shuffle() {
      // simple in-place shuffle
      for (let i = this.products.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [this.products[i], this.products[j]] = [this.products[j], this.products[i]];
      }
    }
  }
};
</script>

<style scoped>
/* optional tweaks */
</style>

<template>
  <div class="card h-100 shadow-sm">
    <img :src="product.image" class="card-img-top" :alt="product.name" style="object-fit:cover; height:160px;">
    <div class="card-body d-flex flex-column">
      <h5 class="card-title mb-2">{{ product.name }}</h5>
      <p class="card-text mb-3 text-muted">{{ product.description }}</p>

      <div class="mt-auto d-flex justify-content-between align-items-center">
        <div class="fw-bold fs-5">${{ formattedPrice }}</div>
        <button class="btn btn-sm btn-outline-primary" @click="$emit('add-to-cart', product)">Add</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    product: { type: Object, required: true }
  },
  computed: {
    formattedPrice() {
      return Number(this.product.price).toFixed(2);
    }
  }
};
</script>

<style scoped>
.card-img-top {
  border-top-left-radius: calc(.25rem - 1px);
  border-top-right-radius: calc(.25rem - 1px);
}
</style>

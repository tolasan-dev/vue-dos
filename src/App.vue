<template>
  <div>
    <Navbar />
    <main class="container my-4">
      <router-view />
    </main>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
export default { components: { Navbar } };
</script>

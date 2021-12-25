<template>
  <div>
    <div class="Nav"><Navbar /></div>
    <main>
      <div style="padding-top: 60px"></div>
      <div class="container">
        <nuxt />
      </div>
    </main>
    <Footer />
  </div>
</template>
<script>
import Navbar from "@/components/Navbar.vue";
import Footer from "@/components/Footer.vue";
export default {
  components: {
    Navbar,
    Footer,
  },
};
</script>

<style scoped>
.Nav {
  position: fixed;
  width: 100%;
  z-index: 100;
  background: rgba(255, 255, 255, 0.5);
}
</style>
<template>
  <div class="main">
    <Header />
    <nuxt />
    <Footer />
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
	<script async src="https://cdn.snipcart.com/themes/v3.2.1/default/snipcart.js"></script>

	<div id="snipcart" data-config-modal-style="side" data-api-key="MDYxNWU2OGQtNTYxMC00NzFhLTg5MzEtNWY4YmRhN2RhNzNmNjM3NjQzMjI5NjM4ODA3NjA5" hidden></div>
  </div>
</template>
<script>
import Header from "~/components/Header.vue";
import Footer from "~/components/Footer.vue";

export default {
  components: {
    Header,
    Footer
  }
};
</script>
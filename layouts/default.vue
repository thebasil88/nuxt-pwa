<template>
  <div class="main">
    <Header />
    <nuxt />
    <Footer />
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
	<script async src="https://cdn.snipcart.com/themes/v3.2.1/default/snipcart.js"></script>
	<div id="snipcart" data-config-modal-style="side" data-api-key="MDYxNWU2OGQtNTYxMC00NzFhLTg5MzEtNWY4YmRhN2RhNzNmNjM3NjQzMjI5NjM4ODA3NjA5" hidden></div>
	<script src="https://cdn.onesignal.com/sdks/OneSignalSDK.js" async=""></script>
	<script>
	  window.OneSignal = window.OneSignal || [];
	  OneSignal.push(function() {
		OneSignal.init({
		  appId: "459935f7-9a37-471f-89dc-7f98ac6edac8",
		});
	  });
	</script>
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
<template>
  <div class="max-w-screen-2xl mx-auto px-10">
    <main>
      <div>
        <section class="mb-10" v-for="(guide, index) in guides" :key="index">
          <div class="post-aside mt-4 mb-4">
            <h3 class="mb-5 underline"><nuxt-link :to="guide.attributes.link">{{ guide.attributes.title }}</nuxt-link></h3>
            <p>{{ guide.attributes.description }}</p>
          </div>
          <div class="grid grid-cols-2 sm:grid-cols-3 justify-center gap-8 mb-10">
            <article class="" v-for="(product, index) in guide.attributes.products" :key="index">
              <img :src="product.image" :alt="product.name" width="464" height="464">
              <p class="font-mono">{{product.name}}</p>
              <button
                class="buy-button snipcart-add-item mt-6 py-2 px-4 bg-gradient-to-r from-green-400 to-blue-500 hover:from-pink-500 hover:to-yellow-500 text-white font-bold rounded-full shadow-offset hover:shadow-lg transition duration-300"
                :data-item-id="product.sku"
                :data-item-name="product.name"
                :data-item-price="product.price"
                :data-item-image="product.image"
                :data-item-url="`https://xenodochial-hermann-cd957d.netlify.app/`">
                {{`$${product.price}`}}
              </button>
            </article>
          </div>
        </section>
		<section id="installsection" class="text-center py-8" v-if="deferredPrompt">
			<p class="text-4xl uppercase pb-4">Like our store? Install our App!</p>
			<button @click="install" class="py-2 px-8 text-center rounded-full bg-indigo-600 text-2xl text-white">Install</button>
		</section>
      </div>
    </main>
  </div>
</template>

<script>
import guides from '~/contents/guides/guides.js'

export default {
  data(){
	return {
		deferredPrompt: null
	}
  },
  created() {
    window.addEventListener("beforeinstallprompt", e => {
      e.preventDefault();
	  console.log('before install prompt');
      // Stash the event so it can be triggered later.
      this.deferredPrompt = e;
    });
	window.addEventListener("appinstalled", () => {
      this.deferredPrompt = null;
    });
  },
  async asyncData ({ route }) {
    const promises = guides.map(guide => import(`~/contents/guides/${guide}.md`))
    return { guides: await Promise.all(promises) }
  },
  methods: {
    async dismiss() {
      this.deferredPrompt = null;
    },
    async install() {
      this.deferredPrompt.prompt();
    }
  },
  head() {
    return {
      title: "All posts | Nuxt.js PWA Coffee Shop"
    }
  }
}
</script>
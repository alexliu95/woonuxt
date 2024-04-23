<script lang="ts" setup>
import { tryOnMounted } from '@vueuse/core';

//const { data } = await useAsyncGql('getProductCategories', { first: 6 });
//const productCategories = data.value?.productCategories?.nodes || [];
//const { data } = await useAsyncGql('getProducts', { first: 4 });
//const featureProducts = data.value?.products?.nodes ?? [];

const featureProducts = ref([]);
async function fetchData() {
    const { data } = await useAsyncGql('getProduct', { first: 4 });
    featureProducts.value = data.value?.products?.nodes ?? [];
}

tryOnMounted(fetchData);

useSeoMeta({
  title: `Home`,
  ogTitle: `Finger-Fun`,
  description: `finger-fun.com – the ultimate destination for finger-skilled toys and games.`,
  ogDescription: `finger-fun.com – the ultimate destination for finger-skilled toys and games.`,
  ogImage: ``,
  twitterCard: `summary_large_image`,
});
</script>

<template>
  <main>
    <HeroBanner />

    <section class="container my-16">
        <div class="grid place-content-center">
            <p class="text-center text-sm">Featured Products</p>
            <h2 class="text-lg font-semibold md:text-4xl">Popular Collections</h2>
        </div>
        <div class="grid justify-center grid-cols-2 gap-4 mt-8 md:grid-cols-3 lg:grid-cols-6">
            <span v-for="(product, i) in featureProducts" :key="i" class="w-full" :node="product" />
        </div>
    </section>

    <section class="container my-16">
        <div class="grid place-content-center">
            <p class="text-center text-sm">New Accessories</p>
            <h2 class="text-lg font-semibold md:text-4xl">Popular Accessories</h2>
        </div>
        <div class="grid justify-center grid-cols-2 gap-4 mt-8 md:grid-cols-4 lg:grid-cols-4">
            <NuxtLink :to="`/product-category/decks`" class="relative flex justify-center overflow-hidden border border-white rounded-xl item snap-mandatory snap-x">
                <NuxtImg width="500" height="500" class="absolute inset-0 object-cover w-full h-full skeleton"
                    src="images/cate-board.jpg" alt="finger skateboard decks" title="deck category"
                    loading="lazy" fit="inside" format="webp" densities="x1 x2" />
                <div class="absolute inset-x-0 bottom-0 opacity-50 bg-gradient-to-t from-black to-transparent h-1/2" />
                <span class="relative z-10 mt-auto mb-2 text-sm font-semibold text-white capitalize md:text-base md:mb-4">Decks</span>
            </NuxtLink>
            <NuxtLink :to="`/product-category/decks`" class="relative flex justify-center overflow-hidden border border-white rounded-xl item snap-mandatory snap-x">
                <NuxtImg width="500" height="500" class="absolute inset-0 object-cover w-full h-full skeleton"
                    src="images/cate-mate.jpg" alt="finger skateboard decks" title="deck category"
                    loading="lazy" fit="inside" format="webp" densities="x1 x2" />
                <div class="absolute inset-x-0 bottom-0 opacity-50 bg-gradient-to-t from-black to-transparent h-1/2" />
                <span class="relative z-10 mt-auto mb-2 text-sm font-semibold text-white capitalize md:text-base md:mb-4">Mates</span>
            </NuxtLink>
            <NuxtLink :to="`/product-category/decks`" class="relative flex justify-center overflow-hidden border border-white rounded-xl item snap-mandatory snap-x">
                <NuxtImg width="500" height="500" class="absolute inset-0 object-cover w-full h-full skeleton"
                    src="images/cate-stage.jpg" alt="finger skateboard decks" title="deck category"
                    loading="lazy" fit="inside" format="webp" densities="x1 x2" />
                <div class="absolute inset-x-0 bottom-0 opacity-50 bg-gradient-to-t from-black to-transparent h-1/2" />
                <span class="relative z-10 mt-auto mb-2 text-sm font-semibold text-white capitalize md:text-base md:mb-4">props</span>
            </NuxtLink>
            <NuxtLink :to="`/product-category/decks`" class="relative flex justify-center overflow-hidden border border-white rounded-xl item snap-mandatory snap-x">
                <NuxtImg width="500" height="500" class="absolute inset-0 object-cover w-full h-full skeleton"
                    src="images/cate-truck.jpg" alt="finger skateboard decks" title="deck category"
                    loading="lazy" fit="inside" format="webp" densities="x1 x2" />
                <div class="absolute inset-x-0 bottom-0 opacity-50 bg-gradient-to-t from-black to-transparent h-1/2" />
                <span class="relative z-10 mt-auto mb-2 text-sm font-semibold text-white capitalize md:text-base md:mb-4">Trucks</span>
            </NuxtLink>
        </div>
    </section>

    <!--<section class="container my-16">
      <div class="flex items-end justify-between">
        <h2 class="text-lg font-semibold md:text-2xl">{{ $t('messages.shop.shopByCategory') }}</h2>
        <NuxtLink class="text-primary" to="/categories">{{ $t('messages.general.viewAll') }}</NuxtLink>
      </div>
      <div class="grid justify-center grid-cols-2 gap-4 mt-8 md:grid-cols-3 lg:grid-cols-6">
        <CategoryCard v-for="(category, i) in productCategories" :key="i" class="w-full" :node="category" />
      </div>
    </section>-->
    <section class="container grid gap-4 my-24 md:grid-cols-2 lg:grid-cols-4">
        <div class="grid place-content-center">
            <p class="text-center text-sm">Shop Your Way</p>
            <h2 class="text-lg font-semibold md:text-3xl">Why choose us</h2>
        </div>
      <div class="flex items-center gap-8 p-8 bg-white rounded-lg">
        <NuxtImg src="/icons/shipping-box.svg" width="60" height="60" alt="Free Shipping" loading="lazy" />
        <div>
          <h3 class="text-xl font-semibold">Free Shipping</h3>
          <p class="text-sm">Free shipping on order over $30</p>
        </div>
      </div>
      <div class="flex items-center gap-8 p-8 bg-white rounded-lg">
        <NuxtImg src="/icons/badge-computer-guarantee.svg" width="60" height="60" alt="Money Back" loading="lazy" />
        <div>
          <h3 class="text-xl font-semibold">Peace of Mind</h3>
          <p class="text-sm">30 days money back guarantee</p>
        </div>
      </div>
      <div class="flex items-center gap-8 p-8 bg-white rounded-lg">
        <NuxtImg src="/icons/secure-gdpr-user.svg" width="60" height="60" alt="Secure Payment" loading="lazy" />
        <div>
          <h3 class="text-xl font-semibold">100% Payment Secure</h3>
          <p class="text-sm">Your payment are safe with us.</p>
        </div>
      </div>
    </section>
  </main>
</template>

<style lang="postcss" scoped>
.brand img {
  max-height: min(8vw, 120px);
  object-fit: contain;
  object-position: center;
}
.item {
  scroll-snap-align: start;
  scroll-snap-stop: always;
  aspect-ratio: 4 / 5;
}
</style>

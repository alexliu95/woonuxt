<script setup lang="ts">
const runtimeConfig = useRuntimeConfig();
const img = useImage();

const logoUrl = runtimeConfig?.public?.LOGO ? img(runtimeConfig?.public?.LOGO) : null;
</script>

<template>
  <NuxtLink to="/">
    <img v-if="logoUrl" :src="logoUrl" alt="Logo" class="object-contain h-10" />
    <div v-else class="flex items-center gap-2 text-lg font-bold">
        <NuxtImg src="/images/logo.png" alt="Logo" class="object-contain h-10" />
      <span>Finger-Fun</span>
    </div>
  </NuxtLink>
</template>

<template>
    <div class="relative mx-auto">
      <NuxtImg
        width="1400"
        height="800"
        class="object-cover w-full h-[360px] lg:h-[480px] xl:h-[500px] skeleton"
        src="/images/finger-skyboard-hero.jpg"
        alt="finger skyboard playing scene"
        loading="eager"
        format="webp"
        fit="outside"
        sizes="sm:100vw lg:1400px"
        fetchpriority="high"
        preload />
      <div class="container absolute inset-0 flex flex-col items-start justify-center bg-gradient-to-l from-gray-200 md:bg-none p-8">
        <h1 class="text-3xl text-white font-bold md:mb-4 md:text-4xl lg:text-6xl">New Journey's Begin.</h1>
        <div class="text-white max-w-sm mb-8 text-md font-light lg:max-w-md text-balance">
          <p>Our meticulously crafted fingerboards are designed to provide an authentic skateboarding experience on a miniature scale. </p>
        </div>
        <div class="flex gap-4">
            <NuxtLink class="px-6 py-3 font-bold text-white bg-blue-800 rounded-xl hover:bg-gray-600" to="/products">Shop now</NuxtLink>
            <NuxtLink class="px-6 py-3 font-bold text-white bg-gray-800 rounded-xl hover:bg-gray-600" to="/products">Shop on ETSY</NuxtLink>
        </div>
        
      </div>
    </div>
  </template>
  
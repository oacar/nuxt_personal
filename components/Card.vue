<template>
  <div class="bg-white border card flex flex-col overflow-hidden">
    <img :src="require(`~/assets/${article.img}`)" class="min-w-0">
    <div class="p-6">
      <div class="text-gray-600 uppercase font-semibold tracking-wide">
        <!-- {{ article.beds }} beds &bull; {{ article.baths }} baths -->
      <h4 class="font-semibold min-w-0 text-lg leading-tight break-words">{{ article.title }}</h4>
      </div>
      <div class="mt-2 flex text-md items-center">
          {{article.description}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['article'],
}
</script>

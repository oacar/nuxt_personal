<script>
  export default {
    async asyncData({ $content, params }) {
      // fetch our article here
        const article = await $content('articles', params.slug).fetch()
        const [prev, next] = await $content('articles')
            .only(['title','slug'])
            .sortBy('createdAt','asc')
            .surround(params.slug)
            .fetch()
      return { 
          article ,
          prev,
          next}
    },
    methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    }
 },
 head() {
  return {
    title: this.article.title,
    meta: [
      {
        hid: "description",
        name: "description",
        content: this.article.description,
      },
      {
        hid: "og:title",
        name: "og:title",
        content: this.article.title,
      },
      {
        hid: "og:description",
        name: "og:description",
        content: this.article.description,
      },
      {
        hid: "og:type",
        property: "og:type",
        content: "article",
      },
      {
        hid: "twitter:title",
        name: "twitter:title",
        content: this.article.title,
      },
      {
        hid: "twitter:description",
        name: "twitter:description",
        content: this.article.description,
      },
      {
        hid: "twitter:image",
        name: "twitter:image",
        content: this.article.image,
      },
      {
        hid: "og:image",
        property: "og:image",
        content: this.article.image,
      },
      {
        property: "article:published_time",
        content: this.article.createdAt,
      },
      {
        property: "article:modified_time",
        content: this.article.updatedAt,
      },
      {
        property: "article:tag",
        content: this.article.tags ? this.article.tags.toString() : "",
      }
    ],
  };
}
 }
</script>
<style>
  .nuxt-content h1 {
    font-weight: bold;
    font-size: 22px;
    /* background-color: black; */
  }
  .nuxt-content h2 {
    font-weight: bold;
    font-size: 20px;
  }
  .nuxt-content p {
    margin-bottom: 20px;
  }
  .icon.icon-link {
      background-image: url('~assets/svg/icon-hashtag.svg');
      display: inline-block;
      width: 20px;
      height: 20px;
      background-size: 20px 20px;
  }
</style>

<template>
  <article>
    <h1 class="bg-blue-100 font-bold text-2xl py-4">{{ article.title }}</h1>
    <p>{{ article.description }}</p>
    <!-- <nav>
      <h1>Table of Contents</h1>
      <ul class="list-disc">
        <li v-for="link of article.toc" :key="link.id" :class="{ 'py-2 font-bold': link.depth === 2, 'ml-2 pb-2': link.depth === 3 }"
>
         <NuxtLink :to="`#${link.id}`">{{ link.text }}</NuxtLink>
        </li>
    </ul>
    </nav> -->

    <img :src="article.img" :alt="article.alt" />

    <nuxt-content :document="article" />

    <p>Article last updated: {{ formatDate(article.updatedAt) }}</p>

    <author :author="article.author"/>

    <prev-next :prev="prev" :next="next" class="flex justify-between my-2"/>
    <!-- <pre> {{ article }} </pre> -->
  </article>
</template>

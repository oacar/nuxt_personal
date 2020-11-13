<script>
export default {
  async asyncData ({ $content, params }) {
      const slug = params.slug 
    const articles = await $content('articles')
      .where({
        tags: { $contains: params.slug }
      })
      .fetch()
    return {
      articles, slug
      //$content.params.slug
      //this.$route
    }
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
<div>
  <h1 class = "my-6">Blog Posts with tags : <span style="color: #ff0000">{{this.slug}}</span> </h1>
  <ul>
    <li v-for="article of articles" :key="article.slug">
      <NuxtLink :to="{name: 'blog-slug', params:{slug:article.slug}}">
        <img :src="article.img" />
        <div>
          <h2>{{article.title}}</h2>
          <!-- <p> by {{article.author.name}}</p> -->
          <p> {{article.description}}</p>
        </div>
      </NuxtLink>
    </li>
  </ul>
</div>
</template>

<template>
 <div>
  <h1>Blog Posts</h1>
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

<script>
export default {
    
    props: {
        articles: {
            type: Array,
            required: true
        }
    }
}
</script>
<style scoped>

</style>
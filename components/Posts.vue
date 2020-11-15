<template>
 <div class = "flex flex-col my-16">
  <h1 class="font-bold text-3xl ">Blog Posts</h1>
  <ul class=" grid grid-cols-3 ">
    <li v-for="article of articles" :key="article.slug" class="my-4 mx-4">
      <NuxtLink :to="{name: 'blog-slug', params:{slug:article.slug}}">
        <!-- <img :src="require(`~/assets/${article.img}`)" class = ""/>
        <div>
          <h2 class="font-bold text-xl">- {{article.title}}</h2>
           <p> by {{article.author.name}}</p> 
           <p> {{article.description}}</p>
        </div> -->
        <div>
          <blog-card :article="article"/>
        </div>
      </NuxtLink>
    </li>
  </ul>
 </div>   
</template>

<script>
import BlogCard from './BlogCard.vue'
export default {
  components: { BlogCard },
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
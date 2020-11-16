<template>
 <div class = "flex flex-col my-16">
  <h1 class="font-bold text-3xl ">{{title}}</h1>
  <ul class=" grid grid-cols-3 ">
    <li v-for="article of articles" :key="article.slug" class="my-4 mx-4">
      <NuxtLink v-if="isBlog" :to="{name: 'blog-slug', params:{slug:article.slug}}">
        <!-- <img :src="require(`~/assets/${article.img}`)" class = ""/>
        <div>
          <h2 class="font-bold text-xl">- {{article.title}}</h2>
           <p> by {{article.author.name}}</p> 
           <p> {{article.description}}</p>
        </div> -->
        <div>
          <card :article="article"/>
        </div>
      </NuxtLink>

      <!-- <h1 v-else>{{article.title}}</h1> -->
      <a v-else :href="article.url">
        <div>
          <card :article="article"/>
        </div>
      </a>
    </li>
  </ul>
 </div>   
</template>

<script>
import Card from './Card.vue'
export default {
  components: { Card },
    props: {
        articles: {
            type: Array,
            required: true
        },
        isBlog:{
            type:  Boolean,
            required: true
        },
        title:{
          type: String,
          default: "Blog Posts"
        }
        

    }
}
</script>
<style scoped>
</style>
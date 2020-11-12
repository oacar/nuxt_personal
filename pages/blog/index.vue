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
     async asyncData({$content, params}){
    const articles =  await $content('articles',params.slug)
    .only(['title','description','img','slug','author'])
    .sortBy('createdAt','asc')
    .fetch()
      return{
articles
      } 
    }
  }
   
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
<template>
   <div class="mt-20 text-center">
<footer class="site-footer">
  <p class="powered-by text-xl font-bold">
    <nuxt-link to="/license">LICENSE: CC-BY-SA <br> 
    <i><font-awesome-icon :icon='["fab","creative-commons"]'/></i>
    <i><font-awesome-icon :icon='["fab","creative-commons-by"]'/></i>
    <i><font-awesome-icon :icon='["fab","creative-commons-sa"]'/></i>
</nuxt-link><br>
  </p>
  

  <p class="powered-by">
    © Omer Acar, 2020 · 

    Made with  <i><font-awesome-icon :icon='["fas","heart"]' style="color:#E13D3D"/></i>
 and <i class='favicon'></i> <a href="https://nuxtjs.org/" target="_blank" rel="noopener" >Nuxt.js</a> .
    
  </p>
</footer>
   </div> 
</template>
<script>
export default {
    
}
</script>

<style scoped>
.favicon {
    background-image: url("~static/icon.png");
display: inline-block;
  width: 20px;
  height: 20px;
  background-size: 20px 20px;
}
</style>

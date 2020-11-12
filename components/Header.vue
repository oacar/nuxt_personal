
<template>
  <div class="navBar flex m-auto z-999 sticky h-auto my-12">
        <h2>Hello world</h2>
    <nav class = "sm:flex flex-col sm:flex-row sm:w-auto w-full order-last sm:order-none my-4 sm:my-0 hidden"> 
        <ul class="flex justify-between"> 
            <li v-for="item in mainNavItems" :key="item.id">
            <NuxtLink :to="item.slug" class="relative text-indigo-900 border-b border-transparent hover:text-indigo-300 ml-0 sm:ml-8 mt-3 sm:mt-0">

        {{item.title}}
        </NuxtLink>
            </li> 
    </ul>

    </nav>
  </div>
</template>

<script>
const mainNavItems = [
  {
    title: 'About Me',
    slug: '/'
  },
  {
    title: 'Resume',
    slug: '/resume/'
  },
  {
    title: 'Blog',
    slug: '/blog/'
  },
  {
    title: 'Contact Me',
    slug: '/contact/'
  }
];
export default {
    data: function () {
        return {
        mainNavItems: mainNavItems,
        show: true
        }
    }   ,
    methods: {
        toggleNavbar(){
            this.show = !this.show
        }
    }
}
</script>

<style scoped>

</style>
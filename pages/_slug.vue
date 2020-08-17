<template>
    <div>
    <div v-if="social" class="w-20 h-auto share hidden md:flex flex-col items-center justify-between">
       <a :href="`https://www.facebook.com/sharer.php?u=https://nuxt-content-blog-theme.vercel.app/${article.slug}`" target="_blank" class="mb-5">
           <img src="https://img.icons8.com/color/48/000000/facebook-new.png"  width="45"/>
       </a>
       <a href="#" class="mb-5">
          <img src="https://img.icons8.com/fluent/48/000000/twitter.png" width="45"/>
       </a>
       <a href="#" class="mb-5">
           <img src="https://img.icons8.com/color/48/000000/link.png" width="45"/>
       </a>
    </div>
    <div class="article-head w-full h-auto bg-indigo-200 mb-8">
        <div class="flex flex-col">
            <div class="container mx-auto flex items-center justify-center h-auto">
                <h1 class="text-4xl text-black font-semibold py-10 px-5 text-center">{{article.title}}</h1>
            </div>
             <div class="flex flex-row items-center justify-center pb-10">
                    <img src="https://api.adorable.io/avatars/66/abott@adorable.png" alt="avatar" class="rounded-full h-10 w-10 shadow">
                    <span class="text-base ml-4 text-gray-700">{{article.author}}</span> <span class="text-base ml-4 text-gray-700">|</span> <p class="ml-4">{{ formatDate(article.updatedAt) }}</p>
                    <br>
            </div>
        </div>
    </div>
    <article class="article mx-auto tracking-wide leading-loose text-xl px-5 md:px-0 mb-10">
        {{ article.description }}
       <div class='my-5'>
           <div class="t-heading w-100 bg-black rounded text-white text-center">
                <h3>Table of contents</h3>
            </div>
            <nav class="p-5 bg-gray-200 rounded">
                <div>
                    <ul>
                        <li v-for="(link, i) of article.toc" :key="link.id">
                        <NuxtLink :to="`#${link.id}`" :class="{ 'py-2': link.depth === 2, 'ml-2 pb-2': link.depth === 3 }">{{i+1}}. {{ link.text }}</NuxtLink>
                        </li>
                    </ul>
                </div>
            </nav>
        </div>
        <nuxt-content class="" :document="article" />
        <prev-next :prev="prev" :next="next" />
    </article>
    </div>
</template>
<script>
  export default {
    async asyncData({ $content, params }) {
    const article = await $content(params.slug).fetch()

        const [prev, next] = await $content()
        .only(['title', 'slug',])
        .sortBy('createdAt', 'asc')
        .surround(params.slug)
        .fetch()

        return {
        article,
        prev,
        next
        }
    },
    methods: {
        formatDate(date) {
            const options = { year: 'numeric', month: 'long', day: 'numeric' }
            return new Date(date).toLocaleDateString('en', options)
        },
        updateScroll() {
            this.scrollPosition = window.scrollY
            if(this.scrollPosition > 340){
                this.social  = true
            }
            else{
                this.social = false
            }
        }
    },
    data(){
        return{
            scrollPosition: null,
            social: false
        }
    },
    mounted() {
        window.addEventListener('scroll', this.updateScroll);
        
    }
  }
</script>
<style lang="css">
html {
  scroll-behavior: smooth;
}
.article{
    max-width: 768px!important;
    position: relative;
}
.share{
    position: fixed;
    top: 10rem;
    right: 10rem;
}
.table-of-content{
    position: fixed;
    top: 0;
    right: -10%;
    background-color: black;
    color: #fff;
    z-index: 2;
    padding: 10px 20px;
    width: 300px;
}
pre{
    border-radius: 8px;
}
/* Table */
table {
    width: 100%!important;
    max-width: 100%;
    margin-bottom: 1rem;
    background-color: transparent;
}
thead {
    display: table-header-group;
    vertical-align: middle;
    border-color: inherit;
}
tbody {
    display: table-row-group;
    vertical-align: middle;
    border-color: inherit;
}
tbody tr:nth-of-type(odd) {
    background-color: rgba(0,0,0,.05);
}
.nuxt-content h2 {
font-weight: bold;
font-size: 28px;
}
.nuxt-content h3 {
font-weight: bold;
font-size: 22px;
}
.nuxt-content p {
margin-bottom: 20px;
}
.nuxt-content h1 {
font-size: 2.25rem;
font-weight: 600;  
}
</style>
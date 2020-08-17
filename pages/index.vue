<template>
  <div >
    <div class="featured px-3 py-2 bg-blue-100">
     <div class="container h-auto mx-auto px-3 py-10 flex flex-col" v-for="content in featured" :key="content.slug">
        <p class="ml-3 text-center px-3 inline-block w-24 rounded bg-blue-200">Featured</p>
        <nuxt-link :to="content.slug">
          <h1 class="px-3 text-3xl font-semibold">{{content.title}}</h1>
        <p class="mt-4 text-xl text-gray-900 px-3">
          {{ content.description }}
        </p>
        </nuxt-link>
     </div>
    </div>
    <div class="mx-auto container px-3 mt-8">
      <h1 class="text-4xl font-semibold py-5 px-3">Latest Article</h1>
      <hr class="px-3">
      <ul class="py-5">
        <li v-for="article of articles" :key="article.slug" class="mb-3 hover:bg-gray-100 p-3 rounded">
          <NuxtLink :to="article.slug">
            <div>
              <h2 class="text-xl text-black font-semibold">{{ article.title }}</h2>
            </div>
            <p class="mt-4 text-xl text-gray-900">
              {{ article.description }}
            </p>
          </NuxtLink>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    async asyncData({ $content, params }) {
      const articles = await $content(params.slug)
        .only(['title', 'slug', 'description'])
        .where({ featured: { $eq: true } })
        .sortBy('createdAt', 'asc')
        .fetch()
      const featured = await $content(params.slug)
        .only(['title', 'slug', 'description'])
        .where({ featured: { $eq: false } })
        .sortBy('createdAt', 'asc')
        .fetch()

      return {
        articles,
        featured
      }
    }
  }
</script>
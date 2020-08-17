<template>
  <div class="bg-blue-100 p-8 my-8 rounded">
      <div>
          <h5 class="text-xl text-blue-900">Related Articles</h5>
      </div>
    <div class="flex flex-col justify-between">
        <NuxtLink
        v-if="prev"
        :to="`/${prev.slug}`"
        class="text-base font-bold text-black hover:underline hover:text-blue-700 transition delay-10 duration-300 ease-in-out"
        >
        > {{ prev.title }}
        </NuxtLink>
        <span v-else></span>
        <NuxtLink
        v-if="next"
        :to="`/${next.slug}`"
        class="text-base font-bold text-black hover:underline hover:text-blue-700 transition delay-10 duration-300 ease-in-out"
        >
        > {{ next.title }}
        </NuxtLink>
        <span v-else></span>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      prev: {
        type: Object,
        default: () => null
      },
      next: {
        type: Object,
        default: () => null
      }
    }
  }
</script>
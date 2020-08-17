<template>
  <div>
      <nav class="bg-white px-2 border-gray-100 border-b-2">
        <div class="container mx-auto flex flex-col justify-center md:flex-row md:justify-between md:px-8">
          <div class="flex justify-center items-center">
           <nuxt-link to="/" class="py-3">Logo</nuxt-link>
          </div>
           <div class="-mb-px flex menu justify-between px-3">
            <nuxt-link to="/" class="no-underline text-teal-dark border-b-2 border-blue-700 uppercase tracking-wide font-bold text-xs py-4 mr-8">
                Home
            </nuxt-link>
            <nuxt-link class="no-underline text-grey-dark border-b-2 border-transparent uppercase tracking-wide font-bold text-xs py-4 mr-8" to="/">
                Products
            </nuxt-link>
            <nuxt-link class="no-underline text-grey-dark border-b-2 border-transparent uppercase tracking-wide font-bold text-xs py-4 mr-8" to="/">
                Discounts
            </nuxt-link>
            <nuxt-link class="no-underline text-grey-dark border-b-2 border-transparent uppercase tracking-wide font-bold text-xs py-4" to="/">
                Customers
            </nuxt-link>
           </div>
        </div>
    </nav>
    <Nuxt />
  </div>
</template>

<script>
export default {
  transition: 'page'
}
</script>

<style>
.page-enter-active, .page-leave-active {
  transition: opacity .5s;
}
.page-enter, .page-leave-to {
  opacity: 0;
}
</style>

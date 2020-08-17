<template>
  <div>
    <header class="lg:px-16 px-6 bg-white flex flex-wrap items-center lg:py-0 py-2">
      <div class="flex-1 flex justify-between items-center">
        <nuxt-link to="/">
         <svg width="37" height="20" viewBox="0 0 37 20" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M8.00002 20H0.727295L4.36366 13.1818H11.6364L8.00002 20Z" fill="#00B906"/>
          <path d="M8.00001 6.81818L4.36365 13.1818H11.6364L8.00001 6.81818Z" fill="#2EC232"/>
          <path d="M11.6364 0L8 6.81818H15.2727L11.6364 0Z" fill="#5CCB5F"/>
          <path d="M11.6364 13.1818L8 6.81818H15.2727L18.4545 13.1818H11.6364Z" fill="#2EC232"/>
          <path d="M14.8182 20L11.6364 13.1818H18.4546L14.8182 20Z" fill="#5CCB5F"/>
          <path d="M22.0909 20H14.8182L18.4546 13.1818H25.7273L22.0909 20Z" fill="#00B906"/>
          <path d="M25.7273 13.1818H18.4546L22.091 6.81818L25.7273 13.1818Z" fill="#00B906"/>
          <path d="M29.3637 6.81818H22.0909L25.7273 13.1818H32.5455L29.3637 6.81818Z" fill="#2EC232"/>
          <path d="M28.9091 20L25.7273 13.1818H32.5455L28.9091 20Z" fill="#00B906"/>
          <path d="M36.1818 20H28.9091L32.5455 13.1818L36.1818 20Z" fill="#2EC232"/>
          <path d="M29.3637 6.81818H22.0909L25.7273 0L29.3637 6.81818Z" fill="#5CCB5F"/>
          </svg>
        </nuxt-link>
      </div>

      <label for="menu-toggle" class="pointer-cursor lg:hidden block">
        <svg
          @click="setOpen"
          class="fill-current text-gray-900"
          xmlns="http://www.w3.org/2000/svg"
          width="20"
          height="20"
          viewBox="0 0 20 20"
        >
          <title>menu</title>
          <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z" />
        </svg>
      </label>
      <!-- <input class="hidden" type="checkbox" id="menu-toggle" /> -->

      <div :class="open? 'hidden': 'block'" class="lg:flex lg:items-center lg:w-auto w-full" id="menu">
        <nav>
          <ul class="lg:flex items-center justify-between text-base text-gray-700 pt-4 lg:pt-0">
            <li>
              <nuxt-link to="/"
                class="lg:p-4 py-3 px-2 rounded md:rounded-none  md:px-0 block border-b-2 border-transparent hover:bg-gray-100 mb-2 md:mb-0 md:hover:border-indigo-400"
              >Categories</nuxt-link>
            </li>
            <li>
              <nuxt-link to="/"
                class="lg:p-4 py-3 px-2 rounded md:rounded-none md:px-0 block border-b-2 border-transparent hover:bg-gray-100 mb-2 md:mb-0 md:hover:border-indigo-400"
              >About</nuxt-link>
            </li>
            <li>
              <nuxt-link to="/"
                class="lg:p-4 py-3 px-2 rounded md:rounded-none md:px-0 block border-b-2 border-transparent hover:bg-gray-100 mb-2 md:mb-0 md:hover:border-indigo-400"
              >Support</nuxt-link>
            </li>
            
          </ul>
        </nav>
        <a href="#" class="lg:ml-4 flex items-center justify-start lg:mb-0 mb-4 pointer-cursor">
          <img
            class="rounded-full w-10 h-10 border-2 border-transparent hover:border-indigo-400"
            src="https://avatars2.githubusercontent.com/u/34214453?s=460&u=cb1ed0948a1229eca70d749ef99cbe304c189110&v=4"
            alt="Manas Paul"
          />
        </a>
      </div>
    </header>
    <Nuxt />
  </div>
</template>

<script>
export default {
  transition: "page",
  data(){
    return {
      open : false
    }
  },
  methods : {
    setOpen(){
      this.open = !this.open
    }
  }
};
</script>

<style>
.page-enter-active,
.page-leave-active {
  transition: opacity 0.5s;
}
.page-enter,
.page-leave-to {
  opacity: 0;
}
</style>

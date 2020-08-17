<template>
  <div>
    <header class="lg:px-16 px-6 bg-white flex flex-wrap items-center lg:py-0 py-2">
      <div class="flex-1 flex justify-between items-center">
        <a href="#">
          <svg width="32" height="36" viewBox="0 0 32 36" xmlns="http://www.w3.org/2000/svg">
            <path
              d="M15.922 35.798c-.946 0-1.852-.228-2.549-.638l-10.825-6.379c-1.428-.843-2.549-2.82-2.549-4.501v-12.762c0-1.681 1.12-3.663 2.549-4.501l10.825-6.379c.696-.41 1.602-.638 2.549-.638.946 0 1.852.228 2.549.638l10.825 6.379c1.428.843 2.549 2.82 2.549 4.501v12.762c0 1.681-1.12 3.663-2.549 4.501l-10.825 6.379c-.696.41-1.602.638-2.549.638zm0-33.474c-.545 0-1.058.118-1.406.323l-10.825 6.383c-.737.433-1.406 1.617-1.406 2.488v12.762c0 .866.67 2.05 1.406 2.488l10.825 6.379c.348.205.862.323 1.406.323.545 0 1.058-.118 1.406-.323l10.825-6.383c.737-.433 1.406-1.617 1.406-2.488v-12.757c0-.866-.67-2.05-1.406-2.488l-10.825-6.379c-.348-.21-.862-.328-1.406-.328zM26.024 13.104l-7.205 13.258-3.053-5.777-3.071 5.777-7.187-13.258h4.343l2.803 5.189 3.107-5.832 3.089 5.832 2.821-5.189h4.352z"
            />
          </svg>
        </a>
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

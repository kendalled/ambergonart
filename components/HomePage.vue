<template>
  <!-- todo: rethink pt -->
  <div class="pt-8 bg-gray-50">
    <PageHeader :open="cart" @toggle="cart = !cart" />
    <TailwindCart :shown="cart" @close="closeCart" />
    <main class="my-8">
      <div class="container px-6 mx-auto">
        <div class="h-64 overflow-hidden bg-center bg-cover rounded-md" style="background-image: url('https://images.unsplash.com/photo-1594040226829-7f251ab46d80?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1280&q=80')">
          <div class="flex items-center h-full bg-gray-900 bg-opacity-50">
            <div class="max-w-xl px-10">
              <h2 class="text-2xl font-semibold text-gray-50">
                Custom Rugs &amp; Decor
              </h2>
              <p class="mt-2 text-gray-300">
                Lorem ipsum dolor, sit amet consectetur adipisicing elit. Tempore facere provident molestias ipsam sint voluptatum pariatur.
              </p>
              <button class="flex items-center px-3 py-2 mt-4 text-sm font-medium text-white uppercase bg-blue-600 rounded hover:bg-blue-500 focus:outline-none focus:bg-blue-500">
                <span>Shop Now</span>
                <svg
                  class="w-5 h-5 mx-2"
                  fill="none"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                ><path d="M17 8l4 4m0 0l-4 4m4-4H3" /></svg>
              </button>
            </div>
          </div>
        </div>
        <div class="mt-8 md:flex md:-mx-4">
          <div class="w-full h-64 overflow-hidden bg-center bg-cover rounded-md md:mx-4 md:w-1/2" style="background-image: url('https://images.unsplash.com/photo-1612641605722-60c66c66530c?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=2800&q=80&auto=format&fit=crop&w=750&q=80')">
            <div class="flex items-center h-full bg-gray-900 bg-opacity-50">
              <div class="max-w-xl px-10">
                <h2 class="text-2xl font-semibold text-gray-50">
                  Prints &amp; Sketches
                </h2>
                <p class="mt-2 text-gray-300">
                  Lorem ipsum dolor, sit amet consectetur adipisicing elit. Tempore facere provident molestias ipsam sint voluptatum pariatur.
                </p>
                <button class="flex items-center mt-4 text-sm font-medium text-white uppercase rounded hover:underline focus:outline-none">
                  <span>Shop Now</span>
                  <svg
                    class="w-5 h-5 mx-2"
                    fill="none"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                  ><path d="M17 8l4 4m0 0l-4 4m4-4H3" /></svg>
                </button>
              </div>
            </div>
          </div>
          <div class="w-full h-64 mt-8 overflow-hidden bg-center bg-cover rounded-md md:mx-4 md:mt-0 md:w-1/2" style="background-image: url('https://images.unsplash.com/photo-1611149916119-c6c16eb89f89?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80')">
            <div class="flex items-center h-full bg-gray-900 bg-opacity-50">
              <div class="max-w-xl px-10">
                <h2 class="text-2xl font-semibold text-gray-50">
                  Paintings
                </h2>
                <p class="mt-2 text-gray-300">
                  Lorem ipsum dolor, sit amet consectetur adipisicing elit. Tempore facere provident molestias ipsam sint voluptatum pariatur.
                </p>
                <button class="flex items-center mt-4 text-sm font-medium text-white uppercase rounded hover:underline focus:outline-none">
                  <span>Shop Now</span>
                  <svg
                    class="w-5 h-5 mx-2"
                    fill="none"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                  ><path d="M17 8l4 4m0 0l-4 4m4-4H3" /></svg>
                </button>
              </div>
            </div>
          </div>
        </div>
        <div class="mt-16">
          <h3 class="text-2xl font-medium text-gray-800">
            Latest releases
          </h3>
          <div class="grid grid-cols-1 gap-6 mt-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
            <ProductCard v-for="j in 4" :key="j" />
          </div>
        </div>
        <div class="my-16">
          <h3 class="text-2xl font-medium text-gray-800">
            Hot deals
          </h3>
          <div class="grid grid-cols-1 gap-6 mt-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
            <ProductCard v-for="i in 4" :key="i" />
          </div>
        </div>
      </div>
    </main>

    <footer class="bg-gray-200">
      <div class="container flex items-center justify-between px-6 py-3 mx-auto">
        <a href="#" class="text-xl font-bold text-gray-500 hover:text-gray-400">Amber Gon Art</a>
        <p class="py-2 text-gray-500 sm:py-0">
          &copy; 2021. All rights reserved.
        </p>
      </div>
    </footer>
  </div>
</template>

<script>

export default {
  name: 'HomePage',
  data () {
    return {
      cart: false
    }
  },
  methods: {
    closeCart () {
      this.cart = false
    }
  }
}
</script>

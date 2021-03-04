<template>
  <!-- todo: rethink pt -->
  <div class="pt-8 bg-gray-50">
    <PageHeader :open="cart" @toggle="cart = !cart" />
    <TailwindCart :cart="currentCart" :shown="cart" @open="openCart" @remove="removeItem" @close="closeCart" />
    <main class="my-8">
      <div class="container px-6 mx-auto">
        <div class="h-64 overflow-hidden bg-center bg-cover rounded-md" style="background-image: url('https://images.unsplash.com/photo-1594040226829-7f251ab46d80?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1280&q=80')">
          <div class="flex items-center h-full bg-gray-900 bg-opacity-50">
            <div class="max-w-xl px-10">
              <h2 class="text-2xl font-semibold text-gray-50">
                Custom Rugs &amp; Decor
              </h2>
              <p class="mt-2 text-gray-300">
                Decorative rugs of almost any size, made by hand &amp; shipped to you. Have a request? Feel free to ask for a commission.
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
                  A collection of hand drawn sketches as well as silk screen prints. Sold with accompanying frames and shipped with care.
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
                  Original paintings of various styles. Watercolor &amp; oil paintings are my speciality - choose between two framing options.
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
            <ProductCard
              v-for="product in latest"
              :key="product.title"
              :title="product.title"
              :price="product.price"
              :img="product.img"
              @carted="addToCart(product)"
            />
          </div>
        </div>
        <div class="my-16">
          <h3 class="text-2xl font-medium text-gray-800">
            Hot deals
          </h3>
          <div class="grid grid-cols-1 gap-6 mt-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
            <ProductCard v-for="product in sales" :key="product.title" :title="product.title" :price="product.price" />
          </div>
        </div>
      </div>
    </main>

    <footer class="bg-gray-200">
      <div class="container flex flex-col justify-between px-6 py-3 mx-auto sm:items-center sm:flex-row">
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
      cart: false,
      currentCart: [],
      latest: [
        {
          title: 'Psychedelic Rug',
          price: 49.99,
          freeShipping: false,
          sale: false,
          img: 'https://images.unsplash.com/photo-1594040226829-7f251ab46d80?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=376&q=80'
        },
        {
          title: 'Marble Vase',
          price: 109.99,
          freeShipping: true,
          sale: false,
          img: 'https://images.unsplash.com/photo-1529136490842-e2da7a4c7b74?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&crop=focalpoint&fp-x=.35&fp-y=1.25&fp-z=3&w=376&q=80'
        },
        {
          title: 'Sketched Portraits',
          price: 34.99,
          freeShipping: false,
          sale: false,
          img: 'https://images.unsplash.com/photo-1612641605722-60c66c66530c?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=376&q=80'
        },
        {
          title: 'Modernist Rug',
          price: 89.99,
          freeShipping: false,
          sale: false,
          img: 'https://images.unsplash.com/photo-1569237601515-99a8a113dc6f?ixlib=rb-1.2.1&auto=format&fit=crop&w=376&q=80'
        }
      ],
      sales: [
        {
          title: 'Minimalist Animal Prints',
          price: 14.99,
          freeShipping: false,
          sale: true,
          img: 'https://images.unsplash.com/photo-1563170351-be82bc888aa4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=376&q=80'
        },
        {
          title: 'Desk Toys',
          price: 19.99,
          freeShipping: false,
          sale: true,
          img: 'https://images.unsplash.com/photo-1563170351-be82bc888aa4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=376&q=80'
        },
        {
          title: 'Custom Bracelets',
          price: 10.99,
          freeShipping: false,
          sale: false,
          img: 'https://images.unsplash.com/photo-1563170351-be82bc888aa4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=376&q=80'
        },
        {
          title: 'Watercolor Paintings',
          price: 25.99,
          freeShipping: false,
          sale: true,
          img: 'https://images.unsplash.com/photo-1563170351-be82bc888aa4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=376&q=80'
        }
      ]
    }
  },
  methods: {
    removeItem (product) {
      this.currentCart.splice(this.currentCart.indexOf(product))
    },
    openCart () {
      this.cart = true
    },
    closeCart () {
      this.cart = false
    },
    addToCart (product) {
      this.currentCart.push(product)
    }
  }
}
</script>

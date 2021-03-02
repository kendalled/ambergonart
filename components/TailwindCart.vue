<template>
  <!-- This example requires Tailwind CSS v2.0+ -->
  <div v-show="showWrapper" class="fixed inset-0 overflow-hidden">
    <div class="absolute inset-0 overflow-hidden">
      <transition
        appear
        enter-active-class="duration-500 ease-in-out"
        enter-class="opacity-0"
        enter-to-class="opacity-100"
        leave-active-class="duration-500 ease-in-out"
        leave-class="opacity-100"
        leave-to-class="opacity-0"
      >
        <div v-if="cartOpen" class="absolute inset-0 transition-opacity bg-gray-500 bg-opacity-75" :aria-hidden="cartOpen" @click="emitClose" />
      </transition>

      <section class="absolute inset-y-0 right-0 flex max-w-full pl-10" aria-labelledby="slide-over-heading">
        <transition
          appear
          enter-active-class="transition duration-500 ease-in-out transform sm:duration-700"
          enter-class="translate-x-full"
          enter-to-class="translate-x-0"
          leave-active-class="transition duration-500 ease-in-out transform sm:duration-700"
          leave-class="translate-x-0"
          leave-to-class="translate-x-full"
          @after-leave="showWrapper = false"
        >
          <div v-if="cartOpen" class="w-screen max-w-md">
            <div class="flex flex-col h-full py-6 overflow-y-scroll bg-white shadow-xl">
              <div class="px-4 sm:px-6">
                <div class="flex items-start justify-between">
                  <h2 id="slide-over-heading" class="text-lg font-medium text-gray-900 lg:text-xl">
                    Your cart
                  </h2>
                  <div class="flex items-center ml-3 h-7">
                    <button class="text-gray-400 bg-white rounded-md hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500" @click="emitClose">
                      <span class="sr-only">Close panel</span>
                      <!-- Heroicon name: outline/x -->
                      <svg
                        class="w-6 h-6"
                        xmlns="http://www.w3.org/2000/svg"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke="currentColor"
                        aria-hidden="true"
                      >
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                      </svg>
                    </button>
                  </div>
                </div>
              </div>
              <div class="relative flex-1 px-4 mt-6 sm:px-6">
                <!-- Replace with your content -->
                <CheckoutItem v-for="item in currentCart" :key="item" :item-title="item" />

                <div class="mt-8">
                  <form class="flex items-center justify-center">
                    <input class="w-full px-4 py-2 bg-gray-100 rounded-md focus:outline-none focus:bg-gray-50 focus:ring-2 focus:ring-blue-300" type="text" placeholder="Add promocode">
                    <button class="flex items-center px-3 py-2 ml-3 text-sm font-medium text-white uppercase bg-blue-600 rounded hover:bg-blue-500 focus:outline-none focus:bg-blue-500">
                      <span>Apply</span>
                    </button>
                  </form>
                </div>
                <a class="flex items-center justify-center px-3 py-2 mt-4 text-sm font-medium text-white uppercase bg-blue-600 rounded hover:bg-blue-500 focus:outline-none focus:bg-blue-500">
                  <span>Checkout</span>
                  <svg
                    class="w-5 h-5 mx-2"
                    fill="none"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                  ><path d="M17 8l4 4m0 0l-4 4m4-4H3" /></svg>
                </a>
                <!-- /End replace -->
              </div>
            </div>
          </div>
        </transition>
      </section>
    </div>
  </div>
</template>

<script>

export default {
  name: 'TailwindCart',
  props: {
    shown: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      showWrapper: false,
      cartOpen: false,
      currentCart: [
        'Custom Rug',
        'Awesome Painting',
        'Cool Drawing'
      ]
    }
  },
  watch: {
    shown (newVal) {
      if (newVal) {
        this.showWrapper = true
        this.cartOpen = true
      }
    }
  },
  methods: {
    emitClose () {
      if (this.cartOpen) {
        this.cartOpen = false
        this.$emit('close')
      }
    }
  }
}
</script>

<template>
  <!-- product item -->
  <div class="flex justify-between mt-6">
    <div class="flex">
      <img class="object-cover w-20 h-20 rounded" :src="img" alt="">
      <div class="mx-3">
        <h3 class="text-sm text-gray-600">
          {{ itemTitle }}
        </h3>
        <div class="flex items-center mt-2">
          <button title="Decrease quantity" class="text-gray-500 focus:outline-none focus:text-gray-600" @click.prevent="decreaseQty">
            <svg
              class="w-5 h-5"
              fill="none"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              viewBox="0 0 24 24"
              stroke="currentColor"
            ><path d="M15 12H9m12 0a9 9 0 11-18 0 9 9 0 0118 0z" /></svg>
          </button>
          <span class="mx-2 text-gray-700">{{ quantity }}</span>
          <button title="Increase quantity" class="text-gray-500 focus:outline-none focus:text-gray-600" @click.prevent="increaseQty">
            <svg
              class="w-5 h-5"
              fill="none"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              viewBox="0 0 24 24"
              stroke="currentColor"
            ><path d="M12 9v3m0 0v3m0-3h3m-3 0H9m12 0a9 9 0 11-18 0 9 9 0 0118 0z" /></svg>
          </button>
        </div>
      </div>
    </div>
    <div class="flex flex-col items-end">
      <span class="text-right text-gray-600">${{ roundToTwo(price * quantity) }}<span v-if="quantity > 1" class="block text-xs text-gray-500">(${{ price }} x {{ quantity }})</span></span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CheckoutItem',
  props: {
    itemTitle: {
      type: String,
      default: 'Product name missing'
    },
    price: {
      type: Number,
      default: 19.99
    },
    img: {
      type: String,
      default: 'https://images.unsplash.com/photo-1563170351-be82bc888aa4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=376&q=80'
    }
  },
  data () {
    return {
      quantity: 1
    }
  },
  methods: {
    roundToTwo (num) {
      return +(Math.round(num + 'e+2') + 'e-2')
    },
    increaseQty () {
      if (this.quantity < 99) {
        this.quantity += 1
      }
    },
    decreaseQty () {
      if (this.quantity > 1) {
        this.quantity -= 1
      } else {
        this.$emit('remove')
      }
    }
  }
}
</script>

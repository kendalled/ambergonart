<template>
  <main class="flex min-h-screen bg-gray-50 justify-center items-center">
    <button class="bg-blue-500 text-blue-50 px-4 py-2 rounded font-medium" @click="login">
      Log in
    </button>
    <button class="bg-blue-500 ml-8 text-blue-50 px-4 py-2 rounded font-medium" @click="signup">
      Sign up
    </button>
    <div id="netlify-modal" />
  </main>
</template>

<script>
import netlifyIdentity from 'netlify-identity-widget'

export default {
  mounted () {
    netlifyIdentity.init({
      container: '#netlify-modal', // defaults to document.body
      locale: 'en' // defaults to 'en'
    })
  },
  methods: {
    login () {
      netlifyIdentity.open('login')
    },
    signup () {
      netlifyIdentity.open('signup')
    }
  }
}
</script>

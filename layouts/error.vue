<template>

  <div class=" w-full justify-center   flex">
    <div class="w-1/2">

      <div class="flex h-full w-full justify-center items-center">
        <svg xmlns="http://www.w3.org/2000/svg" width="90" height="90"
             fill="#DBE1EC" viewBox="0 0 48 48 ">
          <path
            d="M22 30h4v4h-4zm0-16h4v12h-4zm1.99-10C12.94 4 4 12.95 4 24s8.94 20 19.99 20S44 35.05 44 24 35.04 4 23.99 4zM24 40c-8.84 0-16-7.16-16-16S15.16 8 24 8s16 7.16 16 16-7.16 16-16 16z"/>
        </svg>

      </div>
      <div class="text-2xl flex h-full w-full justify-center items-center">
        <h1> {{ message }}
        </h1>
      </div>
      <div class="title flex h-full w-full justify-center items-center">
        <p v-if="statusCode === 404">
          <nuxt-link to="/" class=" mx-auto button zoom text-black  ">
            Return to homepage
          </nuxt-link>
        </p>
      </div>

    </div>
  </div>
</template>
<script>
  export default {
    name: 'NuxtError',
    props: {
      error: {  // <--- Send in the error
        type: Object,
        default: null
      }
    },
    head() {
      return {
        title: this.message // <--- Set the SEO title
      }
    },
    computed: {
      statusCode() {  // <--- Get the status code
        return (this.error && this.error.statusCode) || 500
      },
      message() {  // <--- Print the error
        return this.error.message
      }
    }
  }
</script>

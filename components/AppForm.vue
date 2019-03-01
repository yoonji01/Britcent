<template class>
  <div class="bg-gradient-brand  py-10">
    <h1 class="text-center mb-12 text-4xl">
      {{ componentTitle }}
    </h1>

    <div class="container l:flex justify-center">
      <div class="bg-white p-10  m-5 mt-0 l:w-2/3 border-grey-lighter border-solid border-2 rounded-sm shadow">
        <form
          name="contact"
          action=""
          method="post"
          netlify-honeypot="bot-field"
        >
          <input
            type="hidden"
            name="form-name"
            value="contact"
          >
          <p style="display: none;">
            <label>Don’t fill this out: <input name="bot-field"></label>
          </p>

          <div class="mb-3">
            <label
              for="name"
              class="block text-grey-darkest font-bold md:text-right mb-1 md:mb-0 pr-4"
            >
              Your name
            </label>
            <input
              v-model="name"
              v-validate="'required'"
              type="text"
              name="name"
              data-vv-name="name"
              class="bg-grey-lighter appearance-none border-2 border-grey-lighter rounded w-full py-2 px-4 text-grey-darker leading-tight focus:outline-none focus:bg-white focus:border-blue"
            >
          </div>

          <div class="mb-3">
            <label
              for="email"
              class="block text-grey-darkest font-bold md:text-right mb-1 md:mb-0 pr-4"
            >
              Email
            </label>
            <input
              v-validate="'email|required'"
              type="text"
              data-vv-as="email"
              name="email"
              class="bg-grey-lighter appearance-none border-2 border-grey-lighter rounded w-full py-2 px-4 text-grey-darker leading-tight focus:outline-none focus:bg-white focus:border-blue ns:1/2"
            >
          </div>

          <div class="mb-3">
            <label
              for="message"
              class="block text-grey-darkest font-bold md:text-right mb-1 md:mb-0 pr-4"
            >
              Message:
            </label>
            <textarea
              v-validate="'required'"
              name="message"
              data-vv-as="message"
              class="bg-grey-lighter appearance-none border-2 border-grey-lighter rounded w-full h-32 text-grey-darker leading-tight focus:outline-none focus:bg-white focus:border-blue"
              style="vertical-align: top;"
            />
          </div>

          <div class="flex justify-end">
            <input
              class="shadow bg-blue hover:bg-blue-light focus:shadow-outline focus:outline-none text-white font-bold py-2 px-4 rounded cursor-pointer"
              type="button"
              value="Submit"
              @click="submit"
            >
          </div>
        </form>
      </div>
      <div class="bg-white p-10  m-5 mt-0 l:w-1/3 border-grey-lighter border-solid border-2 rounded-sm shadow">
        <h2 class="leading-tight text-lg mb-3 font-bold ">
          {{ componentHeader }}
        </h2>
        <p class="leading-normal mt-0 mb-5">
          {{ componentParagraph }}
        </p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    componentTitle: {
      type: String,
      required: true
    },
    componentHeader: {
      type: String,
      required: true
    },
    componentParagraph: {
      type: String,
      required: true
    }
  },
  $_veeValidate: {
    validator: 'new'
  },
  // name: "form",
  data() {
    return {
      name: '',
      email: '',
      select: null
    }
  },
  methods: {
    submit() {
      this.$validator.validateAll()
    },
    clear() {
      this.name = ''
      this.email = ''
      this.select = null
      this.checkbox = null
      this.$validator.reset()
    }
  }
}
</script>

<style lang="scss" scoped>
.messageError {
  @apply text-red-light;
  @apply my-1;
}
</style>

<template>
  <div>
    <div
      :style="{'background-image' : 'url('+componentImage+')'}"
      class="bg-cover bg-center ns:h-screen relative relative bg-blue"
    >
      <div class="container h-full relative ns:flex flex-col justify-center pt-32 pb-24 ns:h-100 z-10">
        <div class="text-white m:w-3/5 l:w-2/5">
          <h1
            v-if="componentTitle"
            class="text-point font-majorMonoDisplay mt-20 f1 mb-2 text-5xl l:text-headline leading-tight"
          >
            {{ componentTitle }}
          </h1>
          <p
            v-if="componentParagraph"
            class="text-white mt-0 f1 mb-12 text-3xl leading-normal"
          >
            {{ componentParagraph }}
          </p>
          <form
            v-if="componentForm == true"
            id="signup"
            class="bg-grey-light h-16 flex justify-stretch my-4 p-2 rounded"
          >
            <input
              class="bg-grey-lighter mr-4 appearance-none flex-grow border-2 h-full border-grey-lighter rounded py-2 px-4 text-grey-darker leading-tight focus:outline-none focus:bg-white focus:border-blue"
              placeholder="Enter your email"
              type="email"
              required=""
            >
            <button class="bg-blue-light hover:bg-blue text-grey-lightest font-bold py-4 px-4 rounded inline-flex items-center border-b-4 border-blue-dark">
              Get Started
            </button>
          </form>
          <div v-else>
            <div v-if="componentMailto">
              <a
                href="mailto:enquiries@brightworld.co.uk"
                class="no-underline bg-blue-light hover:bg-blue text-grey-lightest font-bold py-4 px-4 rounded inline-flex items-center border-b-4 border-blue-dark"
              >
                Contact Us
              </a>
            </div>
            <div v-else-if="componentButton">
              <a
                :href="componentLink"
                class="no-underline bg-blue-light hover:bg-blue text-grey-lightest font-bold py-3 px-4 rounded inline-flex items-center border-b-4 border-blue-dark"
              >
                {{ componentButton }}
              </a>
            </div>
          </div>
        </div>
      </div>
      <div
        class="overlay"
        style="background-image: linear-gradient(205deg,rgba(37, 37, 37, 0.23), rgba(10, 10, 10, 0.72));"
      />
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
    componentImage: {
      type: String,
      required: true
    },
    componentParagraph: {
      type: String,
      required: false,
      default: ''
    },
    componentButton: {
      type: Boolean,
      required: false,
      default: true
    },
    componentForm: {
      type: Boolean,
      required: false,
      default: false
    },
    componentMailto: {
      type: Boolean,
      required: false,
      default: false
    },
    componentLink: {
      type: Array,
      required: false,
      default: () => []
    }
  }
}
</script>

<style lang="scss">
.overlay {
  position: absolute;
  @apply pin;
  z-index: 1;
  display: block;
}
</style>

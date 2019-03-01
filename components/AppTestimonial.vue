<template lang="html">
  <section>
    <div class="container py-10">
      <h1 class="text-center mb-12 text-4xl">
        {{ componentTitle }}
      </h1>
      <no-ssr>
        <div
          slot="placeholder"
          class="justify-center items-center flex"
        >
          <font-awesome-icon
            icon="spinner"
            spin
            size="6x"
          />
        </div>
        <carousel
          :auto-play="true"
          :pagination-active-color="'#25324e'"
          :navigation-click-target-size="20"
          :per-page="1"
        >
          <slide
            v-for="(testimonial, index) in componentLoop"
            :key="index"
            class="p-3"
          >
            <figure class="text-center">
              <blockquote class="italic font-normal text-2xl mb-3 text-grey-darker">
                {{ testimonial.quote }}
                <figcaption class="uppercase">
                  <cite class="author font-bold text-sm roman">
                    - {{ testimonial.author }}
                  </cite>
                </figcaption>
              </blockquote>
            </figure>
          </slide>
        </carousel>
      </no-ssr>
      <div class="flex justify-center mt-5">
        <a
          :href="componentLink"
          class="no-underline bg-blue hover:bg-blue-dark text-white font-bold py-2 px-4 rounded self-end"
        >
          {{ componentButton }}
        </a>
      </div>
    </div>
  </section>
</template>


<script>
export default {
  props: {
    componentTitle: {
      type: String,
      required: false,
      default: 'Testimonials'
    },
    componentLoop: {
      type: Array,
      required: true
    },
    componentButton: {
      type: Boolean,
      required: false,
      default: true
    },
    componentLink: {
      type: Array,
      required: false,
      default: () => []
    }
  }
}
</script>

<style scoped lang="scss">
@import '~assets/scss/mixins';
</style>

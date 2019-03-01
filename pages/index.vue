<template>
  <!-- add link to bottom of trusted by -->
  <div>
    <app-main-header
      :component-image="home.image"
      :component-form="false"
      :component-title="home.title"
      :component-paragraph="home.paragraph"
      :component-button="home.header.button"
      :component-link="home.header.href"
    />
    <app-feature-block
      :component-flex-item="'flex-1'"
      :component-title="home.services.title"
      :component-loop="home.services.block"
    />
    <app-feature-Offer
      :component-title="home.offers.title"
      :component-loop="home.offers.block"
    />
    <app-joinus
      :component-background-color="'grey-lightest'"
      :component-title="home.options.title"
      :component-flex-item="'ns:flex-1'"
      :component-loop="home.options.block"
    />
    <app-testimonial
      :component-loop="home.testimonial"
      :component-link="home.testimonialButton.href"
      :component-button="home.testimonialButton.title"
    />
    <app-form
      :component-title="home.form.title"
      :component-header="home.form.header"
      :component-paragraph="home.form.paragraph"
    />
  </div>
</template>

<script>
import home from '~/content/home.json'

import AppMainHeader from '~/components/AppMainHeader.vue'
import AppFeatureBlock from '~/components/AppFeatureBlock.vue'
import AppTestimonial from '~/components/AppTestimonial.vue'
import AppFeatureOffer from '~/components/AppFeatureOffer.vue'
import AppJoinus from '~/components/AppJoinus.vue'
import AppForm from '~/components/AppForm.vue'

export default {
  components: {
    AppMainHeader,
    AppFeatureBlock,
    AppTestimonial,
    AppFeatureOffer,
    AppJoinus,
    AppForm
  },
  data() {
    return {
      home
      // pageTitle: home.title
    }
  },
  head() {
    return {
      title: 'Bright World ' + home.title
    }
  }
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
</style>

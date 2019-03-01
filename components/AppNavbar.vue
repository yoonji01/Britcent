<template>
  <nav
    :class="{ isOpen: isOpen }"
    class="container pt-4 flex justify-end items-center absolute pin-t pin-x w-full z-20 justify-end"
  >
    <!-- <span @click="closeNav(click)" class="pointer z-4">Close</span> -->

    <ul
      class=" list-reset ns:flex  ml-32 flex-wrap  justify-end "
    >
      <li
        v-for="(item, index) in site.nav"
        :key="`nav-${index}`"
        class="ns:mr-4 l:mr-6"
      >
        <a
          :href="item.href"
          class="primary-link text-white no-underline mb-4 text-sm pb-1 border-transparent border-b-2 rounded-sm hover:text-blue"
        >
          {{ item.text }}
        </a>
        <ul
          class="hidden list-reset z-20 relative my-4"
        >
          <li
            v-for="(i, key) in site.nav"
            :key="key"
            class="dib mb-1"
          >
            <a
              :href="i.href"
              class="secondary-link text-white hover:text-blue no-underline text-lg"
            >
              {{ i.text }}
            </a>
          </li>
        </ul>
      </li>
    </ul>

    <span
      v-if="isOpen"
      :class="{ isOpenToggleOpen: isOpen }"
      class="cursor-pointer absolute pin-y pin-r p-4"
      @click="toggleNav()"
    >
      <font-awesome-icon
        icon="times"
        size="2x"
        color="black"
      />
    </span>
    <span
      v-else
      :class="{ isOpenToggleOpen: isOpen }"
      class="cursor-pointer relative z-20"
      @click="toggleNav()"
    >
      <font-awesome-icon
        icon="bars"
        size="2x"
        color="white"
      />
    </span>
    <ul class="hidden absolute pin-t pin-l p-4 list-reset">
      <li>
        <a
          href="#"
          class="no-underline"
        >
          View Our Policies
        </a>
      </li>
    </ul>
  </nav>
</template>

<script>
import site from '~/content/site.json'
import appLogo from '~/components/AppLogo.vue'

export default {
  data() {
    return {
      site,
      isOpen: false,
      appLogo
    }
  },
  methods: {
    closeNav() {},
    toggleNav() {
      this.isOpen = !this.isOpen
      const site = document.querySelector('.site')
      site.classList.toggle('position-fixed')
      // if (site.contains('position-fixed')) {
      //   document.querySelector('#header').classList.remove('position-fixed')
      // } else {
      //   document.querySelector('#header').classList.add('position-fixed')
      // }
      // document.querySelector('header').classList.toggle('h-screen')
    }
  }
}
</script>

<style lang="scss">
@import 'assets/scss/mixins';

// .isOpen {
//   display: block;
//   position: absolute;
//   top: 0;
//   bottom: 0;
//   left: 0;
//   right: 0;
//   width: 100%;
//   z-index: 40;
//   height: 100vh;
//   @apply bg-white;
//   &Toggle {
//     padding-right: 4rem;
//     max-width: 72em;
//   }
// }

.position-fixed {
  height: 100%;
  position: relative;
  overflow: hidden;
  @apply bg-white;
}

.nav--fixed {
  display: flex;
  align-items: center;
  justify-content: flex-end;
}

.nav {
  transition: background-color 0.5s ease;
  @apply bg-transparent;
}

.isOpen {
  position: absolute;
  height: 100vh;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  @apply bg-white;
  @apply text-black;
  z-index: 50;
  justify-content: center;
  @apply p-4;
  &ToggleOpen {
    // display: none;
  }
  &ToggleClose {
    display: block;
  }
  ul {
    display: flex;
    .primary-link {
      @apply text-black;
      @apply border-0;
      @apply text-2xl;
    }
    a {
      @apply text-blue;
    }
    ul {
      display: block;
    }
  }
}

// .pin-important {
//   position: absolute;
//   top: 1.5em;
// }
</style>

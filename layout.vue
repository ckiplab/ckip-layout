<template>
  <div class="Layout min-vh-100 d-flex flex-column bg-milk-light">
    <Nav :fluid="fluid" :toggleable="toggleable">
      <template #brand>
        <slot name="nav-brand" />
      </template>
      <template #body>
        <slot name="nav-body" />
      </template>
      <template #right>
        <slot name="nav-right" />
      </template>
    </Nav>

    <div v-if="fixHeight" class="flex-grow-1 position-relative">
      <div class="position-absolute h-100 w-100">
        <slot />
      </div>
    </div>

    <div v-else class="flex-grow-1">
      <slot />
    </div>

    <Footer :fluid="fluid" :designer="designer">
      <slot name="footer" />
    </Footer>
  </div>
</template>

<script>
import './layout.scss';

import Nav from './nav.vue';
import Footer from './footer.vue';

export default {
  name: 'Layout',
  components: {
    Nav,
    Footer,
  },
  props: {
    fluid: {},
    designer: {},
    toggleable: {},
    fixHeight: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

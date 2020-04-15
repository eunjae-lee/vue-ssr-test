<template>
  <div>
    <p>InstantSearch with index: {{ indexName }}</p>
    <slot />
  </div>
</template>

<script>
export default {
  name: 'InstantSearch',
  props: ['indexName'],
  data() {
    return {
      hello: 'data in InstantSearch.vue',
    };
  },
  inject: {
    instantSearchInstance: {
      name: 'instantSearchInstance',
      default() {
        // const tag = this.$options._componentTag;
        throw new TypeError('It looks like');
      },
    },
  },
};
</script>

<style></style>

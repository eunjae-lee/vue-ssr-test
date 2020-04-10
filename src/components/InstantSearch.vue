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
};
</script>

<style></style>

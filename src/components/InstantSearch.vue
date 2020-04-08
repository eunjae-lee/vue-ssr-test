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
};
</script>

<style></style>

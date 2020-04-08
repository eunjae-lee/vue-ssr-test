<template>
  <div>
    <instant-search :index-name="indexName">
      <configure :hits-per-page="10" :page="1" query="iPhone" />
    </instant-search>
  </div>
</template>

<script>
import InstantSearch from './InstantSearch.vue';
import Configure from './Configure.vue';

export default {
  props: ['indexName'],
  components: {
    InstantSearch,
    Configure,
  },
};
</script>

<style></style>

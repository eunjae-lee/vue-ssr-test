<template>
  <div>
    <p>this is a Configure widget.</p>
    <p>- hitsPerPage: {{ hitsPerPage }}</p>
    <p>- page: {{ page }}</p>
    <p>- query: {{ query }}</p>
  </div>
</template>

<script>
export default {
  name: 'Configure',
  props: ['hitsPerPage', 'page', 'query'],
};
</script>

<style></style>

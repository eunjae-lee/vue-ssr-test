<template>
  <div>
    <p>this is a Configure widget.</p>
    <p>- hitsPerPage: {{ hitsPerPage }}</p>
    <p>- page: {{ page }}</p>
    <p>- query: {{ query }}</p>
  </div>
</template>

<script>
const connector = () => widgetParams => ({
  name: 'Configure',
  widgetParams,
});

export default {
  name: 'Configure',
  props: ['hitsPerPage', 'page', 'query'],
  computed: {
    widgetParams() {
      return {
        hitsPerPage: this.hitsPerPage,
        page: this.page,
        query: this.query,
      };
    },
  },
  inject: {
    instantSearchInstance: {
      name: 'instantSearchInstance',
      default() {
        throw new TypeError('It looks like');
      },
    },
  },
  created() {
    this.factory = connector();
    this.widget = this.factory(this.widgetParams);
    this.instantSearchInstance.addWidgets([this.widget]);
  },
};
</script>

<style></style>

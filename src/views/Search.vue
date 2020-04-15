<template>
  <div>
    <h1>Search</h1>
    <search-main :index-name="indexName" />
  </div>
</template>

<script>
import Vue from 'vue';
import renderToString from 'vue-server-renderer/basic';
import SearchMain from '../components/SearchMain.vue';

function createFakeInstance() {
  return {
    __id: `_${Math.random()
      .toString(36)
      .substr(2, 9)}`,
    widgets: [],
    addWidgets(widgets) {
      this.widgets.push(...widgets);
    },
  };
}

export default {
  name: 'Search',
  components: {
    SearchMain,
  },
  data() {
    return {
      indexName: 'instant_search',
      instantSearchInstance: createFakeInstance(),
    };
  },
  provide() {
    return {
      instantSearchInstance: this.instantSearchInstance,
    };
  },
  serverPrefetch() {
    const app = new Vue(this.$vnode.componentOptions.Ctor);

    return new Promise(resolve => {
      renderToString(app, {}, (err, html) => {
        console.log('renderToString is finished', { err, html });
        console.log('widgets after render', app.instantSearchInstance.widgets);
        resolve();
      });
    });
  },
};
</script>

<style></style>

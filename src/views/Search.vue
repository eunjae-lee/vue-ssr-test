<template>
  <div>
    <h1>Search</h1>
    <search-main :index-name="indexName" />
  </div>
</template>

<script>
import Vue from 'vue';
import SearchMain from '../components/SearchMain.vue';

function renderNode(node) {
  const {
    tag,
    componentOptions: { propsData },
  } = node;

  const childComponent = new node.componentOptions.Ctor({
    _isComponent: true,
    _parentVnode: node,
    parent: node.context.$parent,
  });
  const data = childComponent._data;

  const childNode = childComponent._render();
  const children = childNode.children
    .filter(child => child.componentOptions)
    .map(child => renderNode(child));

  return {
    tag,
    propsData,
    data,
    children,
  };
}

export default {
  name: 'Search',
  serverPrefetch() {
    return new Promise(resolve => {
      const { Ctor } = this.$vnode.componentOptions;
      const app = new Vue({
        render: h => h(Ctor),
      });

      app.$mount();
      const node = app._render();
      console.log(JSON.stringify(renderNode(node), null, 2));
      resolve();
    });
  },
  components: {
    SearchMain,
  },
  data() {
    return {
      indexName: 'instant_search',
    };
  },
};
</script>

<style></style>

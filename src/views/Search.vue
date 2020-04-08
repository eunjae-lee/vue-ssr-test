<template>
  <div>
    <h1>Search</h1>
    <search-main :index-name="indexName" />
  </div>
</template>

<script>
import Vue from 'vue';
// import { createRenderer } from 'vue-server-renderer';
import SearchMain from '../components/SearchMain.vue';

export default {
  name: 'Search',
  serverPrefetch() {
    // return new Promise((resolve, reject) => {
    //   const renderer = createRenderer();
    //   // const { Ctor } = this.$vnode.componentOptions;
    //   // const app = new Vue({
    //   //   render: h => h(Ctor),
    //   // });
    //   const app = new Vue({
    //     render: h => h(SearchMain),
    //   });
    //   renderer.renderToString(app, (err, html) => {
    //     if (err) {
    //       console.log({ err });
    //       reject(err);
    //     } else {
    //       console.log({ html });
    //       resolve();
    //     }
    //   });
    // });

    return new Promise(resolve => {
      const app = new Vue({
        render: h => h(SearchMain),
      });
      app.$mount();
      const node = app._render();
      const child = new node.componentOptions.Ctor();
      const childNode = child._render();
      const firstGrandChild = childNode.children[0];
      console.log({ childNode, firstGrandChild });
      resolve();
    });

    // app.$mount();
    // const vnode = app._vnode;
    // // console.log({
    // //   tag: vnode.tag,
    // //   data: vnode.data,
    // //   children: vnode.children,
    // //   text: vnode.text,
    // //   elm: vnode.elm,
    // //   ns: vnode.ns,
    // //   context: vnode.context,
    // //   key: vnode.key,
    // //   componentOptions: vnode.componentOptions,
    // //   componentInstance: vnode.componentInstance,
    // //   parent: vnode.parent,
    // // });
    // console.log(vnode.context.$options);
    // // console.log({ app });
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

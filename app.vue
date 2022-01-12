<template>
  <div>
    <AisInstantSearch indexName="instant_search" :searchClient="searchClient">
      <AisSearchBox />
      <AisHits />
    </AisInstantSearch>
  </div>
</template>

<script>
import algoliasearch from 'algoliasearch/lite';
import {
  AisInstantSearch,
  AisSearchBox,
  AisHits,
  createServerRootMixin,
} from 'vue-instantsearch/vue3/es';
import { renderToString } from '@vue/server-renderer';
// import { createSSRApp } from 'vue';

const searchClient = algoliasearch(
  'latency',
  '6be0576ff61c053d5f9a3225e2a90f76'
);

export default {
  components: { AisInstantSearch, AisSearchBox, AisHits },
  setup() {
    return {
      searchClient,
    };
  },
  mixins: [
    createServerRootMixin({
      searchClient,
      indexName: 'instant_search',
      // $cloneComponent(componentInstance, { mixins = [] } = {}) {
      //   const options = {
      //     serverPrefetch: undefined,
      //     fetch: undefined,
      //     _base: undefined,
      //     name: 'ais-ssr-root-component',
      //   };

      //   let app;

      //   const appOptions = Object.assign(
      //     {},
      //     componentInstance.$options,
      //     options
      //   );
      //   appOptions.mixins = [
      //     {
      //       beforeCreate() {
      //         this.$nuxt = this.$nuxt || {};
      //       },
      //     },
      //     ...mixins,
      //     ...appOptions.mixins,
      //   ];
      //   app = createSSRApp(appOptions);
      //   if (componentInstance.$router) {
      //     app.use(componentInstance.$router);
      //   }
      //   if (componentInstance.$store) {
      //     app.use(componentInstance.$store);
      //   }

      //   // https://stackoverflow.com/a/48195006/3185307
      //   app.$slots = componentInstance.$slots;
      //   app.$root = componentInstance.$root;
      //   app.$nuxt = {};

      //   return app;
      // },
    }),
  ],
  // serverPrefetch() {
  //   return this.instantsearch
  //     .findResultsState({
  //       component: this,
  //       renderToString,
  //     })
  //     .then((algoliaState) => {
  //       console.log(algoliaState);
  //       // this.$ssrContext.nuxt.algoliaState = algoliaState;
  //     });
  // },
};
</script>

# vue-ssr-test

forked from [https://github.com/1isten/vue-cli-ssr](https://github.com/1isten/vue-cli-ssr).

## Project setup

```
yarn install
```

### Compiles and minifies for production (SSR)

```
npm run build

npm start
```

## Try

Open http://localhost:3000/search and you will see the following log in the terminal:

```json
{
  "tag": "vue-component-3-Search",
  "data": {
    "indexName": "instant_search"
  },
  "children": [
    {
      "tag": "vue-component-5-SearchMain",
      "propsData": {
        "indexName": "instant_search"
      },
      "data": {},
      "children": [
        {
          "tag": "vue-component-7-InstantSearch",
          "propsData": {
            "indexName": "instant_search"
          },
          "data": {
            "hello": "data in InstantSearch.vue"
          },
          "children": [
            {
              "tag": "vue-component-6-Configure",
              "propsData": {
                "query": "iPhone",
                "page": 1,
                "hitsPerPage": 10
              },
              "data": {},
              "children": []
            }
          ]
        }
      ]
    }
  ]
}
```

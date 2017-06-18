
# Backend communication

Projects can be very different in terms of what kind communication they have with different backends. There are countless alternatives for various use cases, and what works best will vary on a project-to-project basis. Some of the alternatives recommended for Vue are listed on [Awesome Vue](https://github.com/vuejs/awesome-vue#http-requests).

## Axios

Axios us a popular simple and generic HTTP communication.

- Axios documentation: [github.com/mzabriskie/axios](https://github.com/mzabriskie/axios)

Axios is already included in this template. If you don't want to use it, simply remove it from `package.json` and remove the part in `ConsolePlugins.vue` where it is used.

## SuperAgent

SuperAgent is another popular generic library for communication.

- [SuperAgent on GitHub](https://github.com/visionmedia/superagent)

## Fetch API

Native Fetch API might be fine for you if you only need low-level network communication, and the browser support is enough for your project.

- [Read more on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

## GraphQL

If you're into GraphQL, Apollo is a popular solution and can be integrated with Vue.

- Integrating Apollo with Vue: [Blog post on Medium](https://dev-blog.apollodata.com/use-apollo-in-your-vuejs-app-89812429d8b2)
- [Apollo Developer documentation](http://dev.apollodata.com/)
- [`vue-apollo`](https://github.com/Akryum/vue-apollo)

## `vue-supply`

For integrating a Vue frontend with advanced and complex technologies such as Meteor, GraphQL or Firebase real-time, you can try `vue-supply` as one alternative.

- [`vue-supply` on GitHub](https://github.com/Akryum/vue-supply)

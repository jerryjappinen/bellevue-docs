
# Routing and pages

```
src/
	└── components/
		└── pages/
			└── PageSomething.vue
	└── config/
		└── config.routes.js
```

We use `vue-router` to handle the routing, so take a look at the docs if you're not familiar with the configuration format.

Official docs: [router.vuejs.org](https://router.vuejs.org/en/)

## Creating pages

Each page we render is simply a Vue component, and each route targets one _component_. To keep things simple, we have components prefixed with `Page` that are only used for this specific purpose, and nothing else, so it's easy to tell pages apart from other components.

The components we use as pages don't have any special functionality, but we generally use the `vue-meta` plugin on only these components.

Each page should be relatively lightweight, and most of its content and functionality should actually be developed as separate components. Think of each page more like a collection of components rather than a functional component in itself.

Page components don't have to be nested in the project structure, and their structure does not have to reflect any specific user-facing navigation elements or menus. That way, we can easily rearrange and unwrap menus in the UI without having to touch internal component structure.

## Configuring a route

Routes are configured in `src/config/config.routes.js`.

```
{
	path: '/',
	name: 'hello',
	component: Hello
}
```

When configuring routes, follow these best practices:

- Avoid unnecessary nesting. Remember that routes don't have to match any specific navigation element or menu 1:1.
- Match the _route_ name with the _page component's_ name.
	- This name should make sense to the developers.
	- This name is not communicated to end-users.
- Choose the route's _path_ in a way that makes sense to end-users.
	- Choose a descriptive and recognisable path for the page.
	- Ensure path has sufficient contrast with other paths.
	- Keep the path short.
	- Avoid underscores and dashes in the path.

## Linking to a page

It's best to link to pages via the route name. That way, if we change any URLs in the frontend, your links will continue to work.

You can use the `<router-link>` component, programmatic navigation or regular anchor elements to link to any page. It's generally desirable to avoid custom click handlers, and stick to something that eventually renders an anchor element, since secondary browser features like tab navigation, copy URL and cmd+click rely on this behavior.

## Route permissions

If you are tracking a current user object in your app, and you want only some pages to be visible to that user, Bellevue becomes preconfigured with simple role-based route guards.

You can define an arbitrary set of roles that works for you, and set the required access level for each route. Any route that's omitted or marked with `0` is accessible by anyone.

```js
// config.base.js
{

	...

	routePermissionRoles: [
		'loggedUser' // 1
	],

	routePermissions: {

		// Root forwards to home, so make sure these two match
		'root': 0,
		'home': 0,

		// Sample pages
		'list': 0,
		'item': 0,

		// Sample page to demo route guards
		'secret': 1

	},

	...

}
```

You need to define how you want to map your backend to these client-side roles in `@models/User.js` and `@services/api/apiAuth.js`.

**Note!** Client-side permission checking is never secure.

## Cleaner URLs without `#`

By default, `vue-router` uses URLs with a `#` character. This can be slightly ugly and slightly confusing to end-users, but the benefit is that for the routing to work, no server-side configuration is needed.

You can get cleaner URLs by setting the router's `mode` to `history` in `src/config/config.base.js`. If you do this, you must ensure that the server you use to serve your app has been configured with appropriate redirects. The docs on [Netlify's redirects for push state](https://www.netlify.com/docs/redirects/#history-pushstate-and-single-page-apps) and [`vue-router` HTML5 history mode](https://router.vuejs.org/en/essentials/history-mode.html) explain this in more detail.

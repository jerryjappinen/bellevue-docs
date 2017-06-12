
# Listing data

Example of a page listing dynamic data with pagination based on routes: [`PageList`](https://github.com/Eiskis/vue-webpack/blob/master/src/components/pages/PageList.vue)

## Blank states

Remember to cover cases when the list you're aiming to render is empty. Each blank state case is different depending on what type of data you're listing and what the business logic behind it is. If you expect the user to do something in order to see something in your list, you should explain this in your blank state visualisation and also provide a button to initiate the creation flow.

Example: [`BlankState`](https://github.com/Eiskis/vue-webpack/blob/master/src/components/snippets/BlankState.vue)

## Using remote data

It's a good pattern to not block the UI while you are fetching remote data. In the component that controls your data presentation, you should keep track of the state of the requests and provide appropriate feedback to the user depending on how long you estimate the loading to take.

As a generic template, the following sample code illustrates the flow.

```js
// MyComponent.vue
export default {
	data: function () {
		return {
			isLoading: false,
			data: null
		};
	},
	computed: {
		isEmpty: function () {
			if (this.data && this.data.length) {
				return false;
			}
			return true;
		}
	},
	methods: {
		fetchData: function () {
			this.isLoading = true;
			// ...
			// In callback, set isLoading back to false
		}
	},
	created: function () {
		this.fetchData();
	}
}
```

In your template, you can now easily react to both `isLoading` and `isEmpty`.

```html
<div class="view-my-component">
	<transition name="transition-fade" mode="out-in">
		<spinner v-if="isLoading"></spinner>
		<template v-else>
			<blank-state v-if="isEmpty" title="No accounts found"></blank-state>
			<div v-else>
				<!-- Here you can finally render your list -->
			</div>
		</template>
	</transition>
</div>
```

## Using models

Instead of working with raw data, it's generally desirable to instantiate [models](../app/models.md) for the data you fetch from the backend. It's generally a good idea to do so immediately after fetching the raw data, so that the components rendering this data can consistently work with all the goodies that come with models.

```js
// ...
axios.get('/api/accounts').then(function (response) {
	vm.data = _.map(response.data, function (item) {
		return new Account({
			propsData: item
		});
	});
});
```

You could also do this the other way around, meaning you let the model object fetch its own data. This works better for individual objects than lists, though.

## Pagination

You can use the `Tabs` component to create simple pagination. It supports both route links and custom callbacks that you can use to set a local `currentPage` value.

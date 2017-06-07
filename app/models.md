
# Models

```
src/
  |__ models/
    |__ MyModel.js
```

Models are **viewless** Vue objects intended for encapsulating business logic in the classical object-oriented way. Viewless in this context means that they have no template, and are never rendered directly.

We use models to encapsulate reusable logic and take advantage of the reactivity and structure provided by Vue. In any practical application, the information architecture should be designed in a way that the same type of data objects are often rendered in multiple different ways.

For example, a user profile typically consists of things like an email, profile picture, full name and a bio, but in the application a profile might be rendered as a list item, thumbnail or a profile page header. In this case, we would write one viewless model for a user profile, and use that in three different components, which do not have to worry about how to combine `firstName` and `lastName` into a computed `fullName`, for example.

If you are fetching data from an API, it's probably a good idea to author roughly equivalent models to the API objects. You can however use models for many other things as well, and also "enhance" the API objects with computed properties and other Vue features as stated in the previous example.

(Note: This example code is not included in the template.)

## Best practices

You should spend a while thinking about what functionality belongs in your models and what doesn't. The same best practices apply for models as for any object-oriented patterns: keep them concise, and use the features Vue provides.

Models should **not** include logic unrelated to the business logic they're encapsulating. If you're writing a lot of helpers, it might be better to move them to [utilities](util.md).

Models should **not** include logic that is purely a one-time presentational concern.

Models **should** however abstract logic that is often needed when representing it in components. You should not completely try to shy away from presentational concerns - after all, that's ultimately why we're writing frontend code.

## Authoring a model

Models are simply viewless Vue objects. They have no template, and we simply export them (without calling `new`) so they can be easily created elsewhere in the codebase.

```js
// src/models/Profile.js
import Vue from 'vue';
export default Vue.extend({
	props: {
		firstName: String,
		lastName: String
	},
	computed: {
		fullName: function () {
			return this.firstName + ' ' this.lastName;
		}
	}
});
```

## Instantiating models

Since in our model we declared which props are accepted to create a `Profile` object, we can now instantiate one in a component file (or anywhere else). We simply create a new `Profile` and pass the property data as [`propsData`](https://vuejs.org/v2/api/#propsData) like with any other Vue object.

```js
// src/components/SomeComponent.vue
import { Profile } from '@models';
var someProfile = new Profile({
	propsData: {
		firstName: 'Foo',
		lastName: 'Bar'
	}
});
console.log(someProfile.fullName); // 'Foo Bar'
someProfile.firstName = 'Bar';
console.log(someProfile.fullName); // 'Bar Bar'
```

## Helpers

You can import some helpers along with the models to reduce a little bit of boilerplate, namely having to wrap the input of a new object as `propsData`.

```js
import { init, Profile } from '@models';
var someProfile = init(Profile, {
	firstName: 'Foo',
	lastName: 'Bar'
});
```

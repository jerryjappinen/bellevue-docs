
# Controls and form elements

```
src/
	|_ components/
  		|_ controls/
  			|_ Click.vue
  			|_ Set.vue
  			|_ Textinput.vue
  			|_ Toggle.vue
		|_ forms/
  			|_ Checkbox.vue
  			|_ Flipswitch.vue
  			|_ Radio.vue
```

Before we talk about form elements, let's summarize the difference between **1-way** and **2-way** data binding. If you're not familiar with this topic, it might also be a good idea to read through the [official documentation on form input bindings](https://vuejs.org/v2/guide/forms.html) before proceeding.

### 1-way data binding

1-way binding means that if you pass a value from a parent component to a child component, the child component can change that value, but the parent component will not receive updates on any changes. Vue has scoped both values and they are independent.

1-way binding is the default in Vue.

### 2-way data binding

2-way binding means that any changes the child makes to the value are also reflected in the parent scope.

Vue requires you to explicitly fire update events to the parent scope, and the parent component to react to those events.

While it requires a bit more work to set up and keep track of 2-way bindings, it also makes the code less magical and allows more granular control over how parent components should react to child components' update events. Vue comes with some syntactic sugar to make this easier, and you can limit using 2-way bindings in `control` components to make it clear which components are read-only and which mutate values in parent scope.

## Form components

While this project template is not intended to be a component library, it does come with a few examples of different components. There are a few different types of control components included.

### Read-write control components

These components use 2-way data binding. These are traditional form elements that both **visualize** and **mutate** values.

Example: [`<Textinput>`](https://github.com/Eiskis/bellevue/blob/master/src/components/controls/Textinput.vue)

### Write-only control components

These components use 2-way data binding. These are components that **only mutate** values. This allows us to abstract certain input behavior (such as toggling a value between `true` and `false` on click), to only one component, and avoid duplicating the same input handling in many components.

This comes in handy in a couple of very common use cases:

1. We're using more than one component in our UI that look different but share the same input logic. A typical example would be checkboxes and toggle switches.
2. We want to control the **hit area** of an input independently of the visual representation of the input. A typical example would be showing a checkbox in a table row and letting the user click anywhere on the row to toggle the checkbox.

- Example: [`<Toggle>`](https://github.com/Eiskis/bellevue/blob/master/src/components/controls/Toggle.vue)
- Example: [`<Click>`](https://github.com/Eiskis/bellevue/blob/master/src/components/controls/Click.vue)

### Read-only form components

These components use 1-way data binding. These are components that represent user-facing form elements, but they **only visualize** values, and do not include any logic for mutating it. Typically these are used inside _controls_ to represent the UI state, which the user can then change by interacting with the _controls_. This pattern is similar to how the `<label>` and `<input>` tags work in standard HTML.

Sometimes you might also use a read-only form component to visualize state without allowing the user to directly change it with a _control_. A typical example would be using a checkbox component to visualize if some computed property is on or off.

- Example: [`<Flipswitch>`](https://github.com/Eiskis/bellevue/blob/master/src/components/forms/Flipswitch.vue)
- Example: [`<Checkbox>`](https://github.com/Eiskis/bellevue/blob/master/src/components/forms/Checkbox.vue)


# Controls and form elements

Before we talk about form elements, let's summarize the difference between **1-way** and **2-way** data binding.

### 1-way data binding

1-way binding means that if you pass a value from a parent component to a child component, the child component can change that value, but the parent component will not receive updates on any changes. Vue has scoped both values and they are independent.

1-way binding is the default in Vue.

### 2-way data binding

2-way binding means that any changes the child makes to the value are also reflected in the parent scope.

Vue requires you to explicitly fire update events to the parent scope, and the parent component to react to those events.

While it requires a bit more work to set up and keep track of 2-way bindings, it also makes the code less magical and allows more granular control over how parent components should react to child components' update events. Vue comes with some syntactic sugar to make this easier, and you can limit using 2-way bindings in `control` components to make it clear which components are read-only and which mutate values in parent scope.

## Form components

While this project template is not intended to be a component library, it does come with a few examples of different components. There are a few different types of components included.

### Read-write control components

These are traditional form elements that both **visualize** and **mutate** values.

Example: [`Textinput.vue`](https://github.com/Eiskis/vue-webpack/blob/master/src/components/controls/Textinput.vue)

### Write-only control components

These are components that **only mutate** values. This allows to abstract certain types of input behavior, such as toggling on and off, to only one component and avoid having to duplicate the same input handling logic elsewhere. This comes in handy in a couple of very common use cases:

1. We're using more than one type of toggle or checkbox components in our UI that share the same behavior but not visual styling or template structure.
2. We want to control the **hit area** of an input independent of the visual representation of the input. For example, the user should be able to press on a long text label next to a checkbox to toggle the checkbox, or anywhere on the table row to toggle a radio button.

This pattern is similar to how the `<label>` and `<input>` tags work in standard HTML.

- Example: [`Toggle.vue`](https://github.com/Eiskis/vue-webpack/blob/master/src/components/controls/Toggle.vue)
- Example: [`Click.vue`](https://github.com/Eiskis/vue-webpack/blob/master/src/components/controls/Click.vue)

### Read-only form components

These are components that represent user-facing form elements, but they **only visualize** values, and do not include any logic for mutating it. Typically these are used inside _controls_ to represent the UI state, which the user can then change by interacting with the _controls_.

Sometimes you might also use a read-only form component to visualize state without allowing the user to directly change it with a control element. A typical use case would be using a checkbox component to visualize if some computed property is true.

- Example: [`Flipswitch.vue`](https://github.com/Eiskis/vue-webpack/blob/master/src/components/forms/Flipswitch.vue)
- Example: [`Checkbox.vue`](https://github.com/Eiskis/vue-webpack/blob/master/src/components/forms/Checkbox.vue)

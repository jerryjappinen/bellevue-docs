
# Getting started

**What practical steps should I take when starting a new project?**

1. Clone [`Eiskis/bellevue`](https://github.com/Eiskis/bellevue)
	- [SSH](git@github.com:Eiskis/bellevue.git)
	- [HTTPS](https://github.com/Eiskis/bellevue.git))
2. Install dependencies with `npm install`
3. Take a quick look at the [application structure diagram](../app/overview.md)?
4. Decide: do you want to use [Vuex](../app/vuex.md)?
	- You can use either services, Vuex or both to implement global state management.
	- If you know Vuex is not for you, you can remove it easily.
	- Keeping Vuex code around won't hurt if you want to decide later.
5. Decide: do you want to use [localisation](../ui/localisation.md)?
	- Localisation can greatly improve the UX for international users
	- It will also increase complexity of your app
	- Ignore or remove it if you don't need it
6. Clean up any other dependencies, sample pages etc. that you don't like
7. Draft the user-facing structure of your app by [adding pages and routes](../ui/routing.md)

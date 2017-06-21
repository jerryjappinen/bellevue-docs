
# Offline support

Providing a good offline experience for your users requires great design and careful consideration of what feature set can and should be available to your users in any given connection status.

What this means varies from project to project. That said, this template comes with the basic tools you need to implement at least basic offline handlign for your users.

## Caching app assets

This template comes with preconfigured support caching the assets needed for running a cached version of your web app. The caching relies on _service workers_ or _appcache_, and is implemented with [`offline-plugin`](https://github.com/NekR/offline-plugin) that is available for Webpack.

You can disable this feature in [configuration](../app/config.md).

## Network service

In your app, during runtime, you can use the [network service](https://github.com/Eiskis/bellevue/blob/master/src/services/network.js) `network` to detect the user's connection status.

`MyComponent.js`

```js
import { network } from '@services';

export default {
	// ...

	computed: function () {

		offlineWarningIsVisible: function () {
			return network.isOffline ? true : false;
		}

		submitButtonEnabled: function () {
			return network.isOnline ? true : false;
		}

	}

	// ...
};

```

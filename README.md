# Svelte-TypeScript-WebPack-Starter

This is a [Svelte](https://svelte.technology/) Starter-Project containing: 

* **Svelte v2.9.9**
* TypeScript
* jQuery 3
* WebPack 4
* Bootstrap 3
* Font-Awesome
* RxJS
* Lodash
* whatwg-fetch

## Demo app

![svelte_demo](http://i.giphy.com/26FKSF8fXF2JD7CZa.gif)

This demo uses [jquery.dataTables](https://datatables.net/) and [Toastr](http://codeseven.github.io/toastr/) plugins.
*Toastr is currently inactive but its package still available.*

## Structure

The core of the app is located in the `init` directory.

* [main.ts](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/init/main.ts) 
* [polyfills.ts](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/init/polyfills.ts)
* [vendor.ts](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/init/vendor.ts)

| File     | Function   | 
| -------------|:---- |
| main.ts   | boots the initial code  |
| polyfills.ts | imports browser polyfills |
| vendor.ts | imports all 3rd party scripts |

`main.ts` contains these two lines of code that instantiate the app. 

```typescript 
import { Main } from 'app/components';
Main('#svelte-app');
```

We import the [Main function](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/app/components/main/main.ts#L4) that takes a CSS selector to hook up the Svelte component. The definition of the component itself is located [main.sve](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/app/components/main/main.sve).

After a successful start the app will also provide a [reference](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/app/components/main/main.ts#L9) to itself in a globally available object `window.app`. 

Of course, this is for testing purposes only. 

<img src="http://i.imgur.com/ya9WMuH.png" width="300" height="350">

There's no rule that Svelte components have to be named with a *.sve extension. It's just my own way of distinguishing between 'ordinary' HTMLs and those containing Svelte code. If you don't like this approach, simply change the regex for svelte-loader in [webpack.common.js](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/config/webpack.common.js#L114).

The Svelte component from this demo is located [here](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/app/components/main/main.sve) and comprises of three parts:

* [Style](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/app/components/main/main.sve#L1) (between `<style>` tags)
* [Structure](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/app/components/main/main.sve#L6) (between `<div>` tags)
* [Logic](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/app/components/main/main.sve#L40) (between `<script>` tags)

I've tried to produce a demo that does something more complex than `Hello World!`

* It fetches JSON-data from a [remote server](http://northwind.servicestack.net/) 
* Presents those data in a nicely looking [table](https://datatables.net/) 
* It even displays a [toast](http://codeseven.github.io/toastr/)! :-)

The fetch-functionality is located in a [separate API](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/app/api/fetch.ts) that'll be of some use to you in more complex scenarios, I hope.

The handling of tabular data is located in a few [custom methods](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/app/components/main/main.sve#L66) that follow [Svelte's rules](https://svelte.technology/guide#custom-methods).

All the Styles are located [here](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/src/app/styling/index.scss).

## WebPack Configuration

Many parts of the webpack configuration are based on the configs from [Angular2-WebPack-Starter](https://github.com/AngularClass/angular2-webpack-starter).

The main [Webpack.config.js](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/webpack.config.js) in the root directory contains a simple `switch` statement that selects the appropriate version depending on your current settings (`prod` or `dev`).

## Installation

```
npm install
```

Then type 

```
npm run start:server
```

to run the app on [http://localhost:3000](http://localhost:3000).

To create a development build type 

```
npm run build:dev
```

Afterwards, either copy the newly created `dist` folder to your web server or type 

```
npm run server:prod
```

to launch a local server on [http://localhost:8080](http://localhost:8080)

For productive builds use `build:prod`.

## License

[MIT](https://github.com/brakmic/Svelte-TypeScript-WebPack-Boilerplate/blob/master/LICENSE)

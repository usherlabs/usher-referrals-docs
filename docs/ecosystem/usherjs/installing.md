---
sidebar_position: 2
---

# Installation

To start submitting tracking referrals & and submitting conversions to Usher, simply copy and paste the snippet below before the end of the Body tag.&#x20;

```html
<script src="https://cdn.jsdelivr.net/npm/@usher.so/js"></script>
```

:::tip
When installing UsherJS on your Web App or dApp, **it is highly recommended to load UsherJS on every page**. This way, no matter where the Campaign redirects your Referred Users, UsherJS is installed to parse the current URL immediately.
:::

If you are producing a JS bundle using Webpack, or some alternative bundler, you can install the JS library directly into your application:

```shell
// npm
npm i @usher.so/js

// yarn
yarn add @usher.so/js
```

The library can then be imported like so:

```javascript
import { Usher } from '@usher.so/js'

const usher = Usher();
usher.parse() // parses the current website URL and saves the referral token to browser storage

```

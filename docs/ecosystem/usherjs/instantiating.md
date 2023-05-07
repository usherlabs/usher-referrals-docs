---
sidebar_position: 3
---

# Instantiating Usher.js

### `Usher(config?)`

Use `Usher(config?)` to create an instance of the **Usher object**. The Usher object is your entrypoint to the rest of the UsherJS SDK.

**Method Parameters**

| Option             | Type          | Default       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ------------------ | ------------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `apiUrl`           | string        | "https://app.usher.so/api" | The URL to the Usher Core API to use for Conversion Tracking                                                                                                                                                                                                                                                                                                                                                                                   |
| `conflictStrategy` | string (enum) | "passthrough" | An enum to indicate how to handle conflicting tokens for the same campaign. The option can be either be `"passthrough"` or `"overwrite"`. In the "passthrough" scenario, referal tokens are backlogged for the same campaign. Any previously tracked referral token is saved to the browser until it expires or is used. In the "overwrite", any new referral token that is saved overwrites other saved tokens relative to the same campaign. |

**Browser HTML Example**

:::note
`window.UsherLoaders` can be used to register a function that will execute when UsherJS loads onto the page.
:::

```html
<script>
  (function () {
    function convert(){
      console.log('Usher loves Arweave!')
      const usher = window.Usher();
      usher.convert({
        id: "QOttOj5CmOJnzBHrqaCLImXJ9RwHVbMDY0QPEmcWptQ",
        chain: "arweave",
        eventId: 0,
        metadata: {
          amount: 100
        }
      });
    }
    if(typeof window.Usher === 'undefined'){
      window.UsherLoaders = window.UsherLoaders || [];
      window.UsherLoaders.push(convert)
    }else{
      convert();
    }
  })();
</script>

```

**Module Example**

```javascript
import { Usher } from '@usher.so/js'

const usher = Usher()
(async () => {
    const conversion = await usher.convert({
        id: "ida4Pebl2uULdI_rN8waEw65mVH9uIFTY1JyeZt1PBM",
        chain: "arweave",
        eventId: 0,
        commit: 10,
        // nativeId: "user_wallet_address",
        metadata: {
            hello: "world",
            key: "value"
        }
    });
    
    console.log('Conversion Result: ', conversion);
})()
```

---
description: >-
  There are two main ways of handling transaction signing: Local Signer and
  Parent Signer.
---

# How to export your Widget

It is controlled by the "Use wallet connection inside the widget - Local Signer" switch on the export page. This choice determines the implementation method;

### 1. Local Signer

Local Signer, is an option with a separate session within the Widget for those looking for simplified implementation. The widget handles the wallet connection and the transaction signing.

### Steps

1. Configure the widget according to your preferences.
2. Copy the iframe embed code.
3. Paste the code in your application code.
4. That’s it!



### 2. Parent Signer:&#x20;

Parent Signer, is a more advanced option and aims to use the existing Parent App's session; it does not need a separate session for the users. If you want to use your existing wallet connection in the widget, you need to install our JS SDK for easy integration.

### Steps

1. First, install the SDK with npm:&#x20;

```
npm install @tinymanorg/tin yman-swap-widget-sdk
```

2. (optional) To get the function parameters easily, you can copy the `Parameters Object` on the export page.&#x20;
3. Then, you should use `generateIframeUrl` to generate the iframe URL, for example:

```
const widgetIframeUrl = WidgetController.generateWidgetIframeUrl({
  platformName: "Platform name",
  // should be `true` if you will use your own wallet
  useParentSigner: true,
  // :exclamation:update `accountAddress` value with the real value of the connected account address
  accountAddress: "ADDRESS_OF_SIGNER_ACCOUNT",
  network: "testnet", // "testnet" or "mainnet"
  themeVariables: {
    shouldDisplayTinymanLogo: true
    // you can customize more styles, please refer to configuration page
  },
  parentUrlOrigin: window.location.origin, // or your app url origin e.g. "https://myapp.com"
  assetIds: [0, 10458941]
});
```

4. Use this URL to add the iframe element to your page:

```
<iframe title="tinyman swap widget"
src=`${widgetIframeUrl}`
style="width: 415px; height: 440px; border: none;"
sandbox="allow-same-origin allow-scripts allow-popups allow-forms"
/>
```

5. Now you should be able to see the widget on your page, but still, you need to establish communication between the application and the widget. We use the `postMessage` API for this. Create an instance of `WidgetController` and set up event listeners with your own callbacks. This way, your application will get a message when the widget needs a signature on a transaction, or when there is an error. And you can send the transaction back to the widget after it’s signed.&#x20;

Please follow our quick start guide here: [https://github.com/tinymanorg/tinyman-swap-widget-sdk#quick-start](https://github.com/tinymanorg/tinyman-swap-widget-sdk#quick-start)

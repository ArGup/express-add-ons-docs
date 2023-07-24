# Script Runtime
The script runtime is a sandboxed JavaScript execution environment based on QuickJS to execute third-party JavaScript code securely and synchronously in another JavaScript environment.

<InlineAlert slots="text" variant="warning"/>

The script runtime references are currently **experimental only**, so you will need to set `experimentalApi` flag to `true` in the [`requirements`](../manifest/index.md#requirements) section of the `manifest.json` to use them. *Please do not use these APIs in any add-ons you plan to distribute or submit with updates until they have been deemed stable.*

## Overview
The script runtime exposes three categories of APIs, which each have their own specific references and are outlined below.

### Communication APIs
The [communication APIs](./communication/) allow you to communicate between the script runtime and the iframe runtime where your add-on is running via exposed APIs.  

### Common APIs
The [common APIs](./common/) are objects and functions injected by the script runtime to allow you the ability to access common utility functions in your JavaScript. 

### Editor APIs
The [editor APIs](./editor/) provide access to the user's document to access the structure and properties, and to make changes to it via high-level authoring APIs. 

## Script Runtime JavaScript Engine
The script runtime is based on [QuickJS](https://bellard.org/quickjs/) and implements a subset of the [ES2020 specification](https://tc39.es/ecma262/). 

Some key concepts to note about the script runtime include:

- Provides limited access to browser APIs (see the [Common APIs](./common/) reference). Note however, you can use the communication APIs to execute browser APIs (ie: `fetch`) in the iframe runtime environment.
- Runs in a slower execution environment.
- Provides no debugging capabilities other than those provided by the [injected `console` functions](../common/index.md#injected-objects).
- Runs in the same context/thread as the host's application business logic, (e.g. the authoring worker thread in Adobe Express), thus providing access to interact with it via the injected APIs.

## Getting Started with the APIs
The methods defined in the [communication API reference](./communication/) are used to expose and use the API proxies between the iframe and script environments of your add-on. Start [there](./communication/) to learn more about how to expose APIs and use them from either runtime environment.

### Script entry point
To use the script runtime in your add-on, start by defining a new `script` entry point in your `manifest.json` file with the value set to the name of the file containing the JavaScript code you're using with the script runtime functions: 

```json
    "entryPoints": [
        {
            "type": "panel",
            "id": "panel1",
            "main": "index.html",
            "script": "code.js" 
        }
    ]
```

The JavaScript code in the file referenced can then access any of the injected global objects and module APIs defined in all of the APIs outlined in this set of references ([communication APIs](./communication/), [common APIs](./common/) and [editor APIs](./editor/).

## Code Samples
The following [code samples](https://github.com/AdobeDocs/express-add-on-samples/tree/main/script-runtime-samples) have been provided to help you get started using these new script runtime APIs.

### [communication-iframe-script-runtime sample](https://github.com/AdobeDocs/express-add-on-samples/tree/main/script-runtime-samples/communication-iframe-script-runtime)
Demonstrates the use of the communication APIs to expose and proxy APIs bidirectionally between the iframe and script runtime environments. Also includes demonstrating how to use some of the [common APIs](./common/) such as `setTimeout()` and `console.log()`.

### [editor-apis sample](https://github.com/AdobeDocs/express-add-on-samples/tree/main/script-runtime-samples/editor-apis)
Demonstrates how to use the [editor APIs](./editor/) to create various shapes and add them to the document. 

### [image-and-page sample](https://github.com/AdobeDocs/express-add-on-samples/tree/main/script-runtime-samples/image-and-page) 
A more comprehensive example of using the [editor APIs](./editor/) to add a page, images and shapes, as well as clear the artboard.
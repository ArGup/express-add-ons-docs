# Drag and Drop
Allows you to drag and drop objects to the document.

<CodeBlock slots="heading, code" repeat="2" languages="JavaScript" />

### Interface

```js
interface DragCompletionData {
  /**
   * Blob (image/video) to be added to the document
   */
  blob: Blob;
}

/**
 * Callback to provide the preview image
 * @returns URL or DataURL
 **/
type DragPreviewCallback = (element: HTMLElement) => URL;

/**
 * Callback to provide the content (image/video) to be added to the document
 **/
type DragCompletionCallback = (
  element: HTMLElement
) => Promise<DragCompletionData[]>;

interface DragCallbacks {
  /**
   * Callback to provide the preview image
   */
  previewCallback: DragPreviewCallback;

  /**
   * Callback to provide the content to be added to the document
   */
  completionCallback: DragCompletionCallback;
}

interface Application {
  /**
   * Enable drag to document functionality for an element
   */
  enableDragToDocument(
    element: HTMLElement,
    dragCallbacks: DragCallbacks
  ): void;
}

/**
 * "dragstart" event is triggered when the user starts dragging an item for which drag behavior is enabled
 *
 * "dragend" event is triggered when the drag operation ends
 */

interface DragStartEventData {
  /**
   * Element for which the drag event started
   */
  element: HTMLElement;
}

interface DragEndEventData {
  /**
   * Drop occurred/Drag ended at invalid position
   */
  dropCancelled: boolean;

  /**
   * Element for which the drag event ended
   */
  element: HTMLElement;
}
```

### Example

```js
import AddOnSdk from "https://new.express.adobe.com/static/add-on-sdk/sdk.js";

// Enable drag support for an element
function makeDraggableUsingUrl(elementId: string, previewUrl: string) {
  const image = document.getElementById(elementId);

  const dragCallbacks = {
    previewCallback: (image: HTMLElement) => {
      return new URL(previewUrl);
    },
    completionCallback: async (image: HTMLElement) => {
      const imageBlob = await fetch(image.src).then((response) =>
        response.blob()
      );
      return [{ blob: imageBlob }];
    },
  };

  try {
    AddOnSdk.app.enableDragToDocument(image, dragCallbacks);
  } catch (error) {
    console.log("Failed to enable DragToDocument:", error);
  }
}

AddOnSdk.app.on("dragstart", (eventData: DragStartEventData) => {
  console.log("The drag event has started for", eventData.element);
});

AddOnSdk.app.on("dragend", (eventData: DragEndEventData) => {
  if (!eventData.dropCancelled) {
    console.log("The drag event has ended for", eventData.element);
  } else {
    console.log("The drag event was cancelled for", eventData.element);
  }
});
```
<InlineAlert slots="text" variant="info"/>

Please note, the maximum dimension of an object dropped on to the canvas in Express is 8000x8000. 

<InlineAlert slots="text" variant="success"/>

Many of the samples we've included in the [code samples](guides/develop/samples) implement the Drag and Drop APIs, so please use them as a reference. This includes the the **import-images-from-local**, **import-images-using-oauth**, **giphy** and **qrcode** samples.
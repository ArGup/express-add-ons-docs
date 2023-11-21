[@express-document-sdk](../overview.md) / ImageRectangleNode

# Class: ImageRectangleNode

ImageRectangleNode is a rectangular node that displays the image media part of a MediaContainerNode. It can only exist
within that container parent. Cropping can be adjusted by changing this media's position/rotation (as well as its mask
shape sibling node).

## Hierarchy

- [`Node`](Node.md)

  ↳ **`ImageRectangleNode`**

## Implements

- `Readonly`<[`IRectangularNode`](../interfaces/IRectangularNode.md)\>

## Table of contents

### Accessors

- [absoluteRotation](ImageRectangleNode.md#absoluterotation)
- [absoluteTransform](ImageRectangleNode.md#absolutetransform)
- [allChildren](ImageRectangleNode.md#allchildren)
- [blendMode](ImageRectangleNode.md#blendmode)
- [height](ImageRectangleNode.md#height)
- [locked](ImageRectangleNode.md#locked)
- [opacity](ImageRectangleNode.md#opacity)
- [parent](ImageRectangleNode.md#parent)
- [relativeRotation](ImageRectangleNode.md#relativerotation)
- [relativeTransform](ImageRectangleNode.md#relativetransform)
- [translateX](ImageRectangleNode.md#translateX)
- [translateY](ImageRectangleNode.md#translateY)
- [type](ImageRectangleNode.md#type)
- [width](ImageRectangleNode.md#width)

### Methods

- [removeFromParent](ImageRectangleNode.md#removefromparent)

## Accessors

### absoluteRotation

• `get` **absoluteRotation**(): `number`

The node's absolute (global) rotation angle in degrees – includes any cumulative rotation from the node's parent containers.

#### Returns

`number`

#### Inherited from

Node.absoluteRotation

• `set` **absoluteRotation**(`value`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

#### Inherited from

Node.absoluteRotation

___

### absoluteTransform

• `get` **absoluteTransform**(): [`mat2d`](https://glmatrix.net/docs/module-mat2d.html)

The node's absolute (global) transform matrix.

#### Returns

[`mat2d`](https://glmatrix.net/docs/module-mat2d.html)

#### Inherited from

Node.absoluteTransform

___

### allChildren

• `get` **allChildren**(): `Readonly`<`Iterable`<[`Node`](Node.md)\>\>

Returns a read-only list of all children of the node. General-purpose content containers such as ArtboardNode or
GroupNode also provide a mutable [children](ContainerNode.md#children) list. Other nodes with a more specific structure can
hold children in various discrete "slots"; this `allChildren` list includes *all* such children and reflects their
overall display z-order.

#### Returns

`Readonly`<`Iterable`<[`Node`](Node.md)\>\>

#### Inherited from

Node.allChildren

___

### blendMode

• `get` **blendMode**(): [`BlendMode`](../enums/BlendMode.md)

Blend mode determines how a node is composited onto the content below it. The default value is
[normal](../enums/BlendMode.md#normal) for most nodes, and [passThrough](../enums/BlendMode.md#passthrough) for GroupNodes.

#### Returns

[`BlendMode`](../enums/BlendMode.md)

#### Inherited from

Node.blendMode

• `set` **blendMode**(`value`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | [`BlendMode`](../enums/BlendMode.md) |

#### Returns

`void`

#### Inherited from

Node.blendMode

___

### height

• `get` **height**(): `number`

Current height of the "full frame" image rectangle, which may not be fully visible due to cropping/clipping by the
enclosing media container's maskShape. This size may be different from the original bitmap's size in pixels, but
will always match its aspect ratio.

#### Returns

`number`

#### Implementation of

Readonly.height

___

### locked

• `get` **locked**(): `boolean`

The node's lock/unlock state. Locked nodes are excluded from the selection (see [selection](Context.md#selection)), and
cannot be edited by the user unless they are unlocked first.

#### Returns

`boolean`

#### Inherited from

Node.locked

• `set` **locked**(`locked`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `locked` | `boolean` |

#### Returns

`void`

#### Inherited from

Node.locked

___

### opacity

• `get` **opacity**(): `number`

The node's opacity, from 0.0 to 1.0

#### Returns

`number`

#### Inherited from

Node.opacity

• `set` **opacity**(`opacity`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `opacity` | `number` |

#### Returns

`void`

#### Inherited from

Node.opacity

___

### parent

• `get` **parent**(): `undefined` \| [`Node`](Node.md)

The node's parent. Undefined if the node is an orphan, or if the node is the artwork root.

#### Returns

`undefined` \| [`Node`](Node.md)

#### Inherited from

Node.parent

___

### relativeRotation

• `get` **relativeRotation**(): `number`

The node's local rotation value in degrees, relative to its parent's axes. Modifying this value will also adjust the
node's x & y translation such that the node's center is in the same location after the rotation – i.e. this setter
rotates the node about its bounding box's center, not its origin.

#### Returns

`number`

#### Inherited from

Node.relativeRotation

• `set` **relativeRotation**(`value`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

#### Inherited from

Node.relativeRotation

___

### relativeTransform

• `get` **relativeTransform**(): [`mat2d`](https://glmatrix.net/docs/module-mat2d.html)

The node's transform matrix relative to its parent.

#### Returns

[`mat2d`](https://glmatrix.net/docs/module-mat2d.html)

#### Inherited from

Node.relativeTransform

___

### translateX

• `get` **translateX**(): `number`

The translation of the node along its parent's x-axis.

#### Returns

`number`

#### Inherited from

Node.translateX

• `set` **translateX**(`value`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

#### Inherited from

Node.translateX

___

### translateY

• `get` **translateY**(): `number`

The translation of the node along its parent's y-axis.

#### Returns

`number`

#### Inherited from

Node.translateY

• `set` **translateY**(`value`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

#### Inherited from

Node.translateY

___

### type

• `get` **type**(): [`SceneNodeType`](../enums/SceneNodeType.md)

The node's type.

#### Returns

[`SceneNodeType`](../enums/SceneNodeType.md)

#### Inherited from

Node.type

___

### width

• `get` **width**(): `number`

Current width of the "full frame" image rectangle, which may not be fully visible due to cropping/clipping by the
enclosing media container's maskShape. This size may be different from the original bitmap's size in pixels, but
will always match its aspect ratio.

#### Returns

`number`

#### Implementation of

Readonly.width

## Methods

### removeFromParent

▸ **removeFromParent**(): `void`

Removes the node from its parent - for a basic ContainerNode, this is equivalent to `node.parent.children.remove(node)`.
For nodes with other slots, removes the child from whichever slot it resides in, if possible. Throws if the slot does
not support removal. Also throws if node is the artwork root. No-op if node is already an orphan.

#### Returns

`void`

#### Inherited from

[Node](Node.md).[removeFromParent](Node.md#removefromparent)
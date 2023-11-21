[@express-document-sdk](../overview.md) / Node

# Class: Node

A Node represents an object in the scenegraph, the document's visual content tree.

## Hierarchy

- `ProxyLiveObject`

  ↳ **`Node`**

  ↳↳ [`ComplexShapeNode`](ComplexShapeNode.md)

  ↳↳ [`ContainerNode`](ContainerNode.md)

  ↳↳ [`ExpressRootNode`](ExpressRootNode.md)

  ↳↳ [`GridLayoutNode`](GridLayoutNode.md)

  ↳↳ [`ImageRectangleNode`](ImageRectangleNode.md)

  ↳↳ [`MediaContainerNode`](MediaContainerNode.md)

  ↳↳ [`PageNode`](PageNode.md)

  ↳↳ [`StrokableNode`](StrokableNode.md)

  ↳↳ [`TextNode`](TextNode.md)

## Table of contents

### Accessors

- [absoluteRotation](Node.md#absoluterotation)
- [absoluteTransform](Node.md#absolutetransform)
- [allChildren](Node.md#allchildren)
- [blendMode](Node.md#blendmode)
- [locked](Node.md#locked)
- [opacity](Node.md#opacity)
- [parent](Node.md#parent)
- [relativeRotation](Node.md#relativerotation)
- [relativeTransform](Node.md#relativetransform)
- [translateX](Node.md#translateX)
- [translateY](Node.md#translateY)
- [type](Node.md#type)

### Methods

- [removeFromParent](Node.md#removefromparent)

## Accessors

### absoluteRotation

• `get` **absoluteRotation**(): `number`

The node's absolute (global) rotation angle in degrees – includes any cumulative rotation from the node's parent containers.

#### Returns

`number`

• `set` **absoluteRotation**(`value`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

___

### absoluteTransform

• `get` **absoluteTransform**(): [`mat2d`](https://glmatrix.net/docs/module-mat2d.html)

The node's absolute (global) transform matrix.

#### Returns

[`mat2d`](https://glmatrix.net/docs/module-mat2d.html)

___

### allChildren

• `get` **allChildren**(): `Readonly`<`Iterable`<[`Node`](Node.md)\>\>

Returns a read-only list of all children of the node. General-purpose content containers such as ArtboardNode or
GroupNode also provide a mutable [children](ContainerNode.md#children) list. Other nodes with a more specific structure can
hold children in various discrete "slots"; this `allChildren` list includes *all* such children and reflects their
overall display z-order.

#### Returns

`Readonly`<`Iterable`<[`Node`](Node.md)\>\>

___

### blendMode

• `get` **blendMode**(): [`BlendMode`](../enums/BlendMode.md)

Blend mode determines how a node is composited onto the content below it. The default value is
[normal](../enums/BlendMode.md#normal) for most nodes, and [passThrough](../enums/BlendMode.md#passthrough) for GroupNodes.

#### Returns

[`BlendMode`](../enums/BlendMode.md)

• `set` **blendMode**(`value`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | [`BlendMode`](../enums/BlendMode.md) |

#### Returns

`void`

___

### locked

• `get` **locked**(): `boolean`

The node's lock/unlock state. Locked nodes are excluded from the selection (see [selection](Context.md#selection)), and
cannot be edited by the user unless they are unlocked first.

#### Returns

`boolean`

• `set` **locked**(`locked`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `locked` | `boolean` |

#### Returns

`void`

___

### opacity

• `get` **opacity**(): `number`

The node's opacity, from 0.0 to 1.0

#### Returns

`number`

• `set` **opacity**(`opacity`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `opacity` | `number` |

#### Returns

`void`

___

### parent

• `get` **parent**(): `undefined` \| [`Node`](Node.md)

The node's parent. Undefined if the node is an orphan, or if the node is the artwork root.

#### Returns

`undefined` \| [`Node`](Node.md)

___

### relativeRotation

• `get` **relativeRotation**(): `number`

The node's local rotation value in degrees, relative to its parent's axes. Modifying this value will also adjust the
node's x & y translation such that the node's center is in the same location after the rotation – i.e. this setter
rotates the node about its bounding box's center, not its origin.

#### Returns

`number`

• `set` **relativeRotation**(`value`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

___

### relativeTransform

• `get` **relativeTransform**(): [`mat2d`](https://glmatrix.net/docs/module-mat2d.html)

The node's transform matrix relative to its parent.

#### Returns

[`mat2d`](https://glmatrix.net/docs/module-mat2d.html)

___

### translateX

• `get` **translateX**(): `number`

The translation of the node along its parent's x-axis.

#### Returns

`number`

• `set` **translateX**(`value`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

___

### translateY

• `get` **translateY**(): `number`

The translation of the node along its parent's y-axis.

#### Returns

`number`

• `set` **translateY**(`value`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

___

### type

• `get` **type**(): [`SceneNodeType`](../enums/SceneNodeType.md)

The node's type.

#### Returns

[`SceneNodeType`](../enums/SceneNodeType.md)

## Methods

### removeFromParent

▸ **removeFromParent**(): `void`

Removes the node from its parent - for a basic ContainerNode, this is equivalent to `node.parent.children.remove(node)`.
For nodes with other slots, removes the child from whichever slot it resides in, if possible. Throws if the slot does
not support removal. Also throws if node is the artwork root. No-op if node is already an orphan.

#### Returns

`void`
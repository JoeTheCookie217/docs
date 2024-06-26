# IFactory

## Table of contents

### Constructors

- [constructor](IFactory.md#constructor)

### Properties

- [\_origin](IFactory.md#_origin)

### Methods

- [addQuoteAsset](IFactory.md#addquoteasset)
- [createLBPair](IFactory.md#createlbpair)
- [getAllLBPairs](IFactory.md#getalllbpairs)
- [getAvailableLBPairBinSteps](IFactory.md#getavailablelbpairbinsteps)
- [getLBPairInformation](IFactory.md#getlbpairinformation)
- [getOwner](IFactory.md#getowner)
- [getPreset](IFactory.md#getpreset)
- [init](IFactory.md#init)
- [setPreset](IFactory.md#setpreset)

## Constructors

### constructor

• **new IFactory**(`at`): [`IFactory`](IFactory.md)

Wraps a smart contract exposing standard token FFI.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `at` | `Address` | Address of the smart contract. |

#### Returns

[`IFactory`](IFactory.md)

#### Defined in

[assembly/interfaces/IFactory.ts:21](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IFactory.ts#L21)

## Properties

### \_origin

• **\_origin**: `Address`

#### Defined in

[assembly/interfaces/IFactory.ts:14](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IFactory.ts#L14)

## Methods

### addQuoteAsset

▸ **addQuoteAsset**(`_asset`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `_asset` | `Address` |

#### Returns

`void`

#### Defined in

[assembly/interfaces/IFactory.ts:123](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IFactory.ts#L123)

___

### createLBPair

▸ **createLBPair**(`_tokenA`, `_tokenB`, `_activeId`, `_binStep`, `_masToSend`): `Address`

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `_tokenA` | `Address` | address of the first token |
| `_tokenB` | `Address` | address of the second token |
| `_activeId` | `u32` | active id disired |
| `_binStep` | `u32` | bin step disired |
| `_masToSend` | `u64` | Massa to send for storage |

#### Returns

`Address`

the address of the new LBPair

**`Dev`**

Create a new LBPair

#### Defined in

[assembly/interfaces/IFactory.ts:83](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IFactory.ts#L83)

___

### getAllLBPairs

▸ **getAllLBPairs**(`_tokenX`, `_tokenY`): [`LBPairInformation`](../structs/LBPairInformation.md)[]

#### Parameters

| Name | Type |
| :------ | :------ |
| `_tokenX` | `Address` |
| `_tokenY` | `Address` |

#### Returns

[`LBPairInformation`](../structs/LBPairInformation.md)[]

#### Defined in

[assembly/interfaces/IFactory.ts:46](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IFactory.ts#L46)

___

### getAvailableLBPairBinSteps

▸ **getAvailableLBPairBinSteps**(`_tokenA`, `_tokenB`): `u32`[]

#### Parameters

| Name | Type |
| :------ | :------ |
| `_tokenA` | `Address` |
| `_tokenB` | `Address` |

#### Returns

`u32`[]

#### Defined in

[assembly/interfaces/IFactory.ts:128](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IFactory.ts#L128)

___

### getLBPairInformation

▸ **getLBPairInformation**(`_tokenA`, `_tokenB`, `_binStep`): [`LBPairInformation`](../structs/LBPairInformation.md)

#### Parameters

| Name | Type |
| :------ | :------ |
| `_tokenA` | `Address` |
| `_tokenB` | `Address` |
| `_binStep` | `u64` |

#### Returns

[`LBPairInformation`](../structs/LBPairInformation.md)

#### Defined in

[assembly/interfaces/IFactory.ts:36](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IFactory.ts#L36)

___

### getOwner

▸ **getOwner**(): `Address`

#### Returns

`Address`

#### Defined in

[assembly/interfaces/IFactory.ts:134](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IFactory.ts#L134)

___

### getPreset

▸ **getPreset**(`binstep`): [`Preset`](../structs/Preset.md)

#### Parameters

| Name | Type |
| :------ | :------ |
| `binstep` | `u32` |

#### Returns

[`Preset`](../structs/Preset.md)

#### Defined in

[assembly/interfaces/IFactory.ts:138](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IFactory.ts#L138)

___

### init

▸ **init**(`_feeRecipient`, `_flashLoanFee?`): `void`

Initialize the factory. This function must be called before any other function.

#### Parameters

| Name | Type | Default value | Description |
| :------ | :------ | :------ | :------ |
| `_feeRecipient` | `Address` | `undefined` | The address of the fee recipient |
| `_flashLoanFee` | `u256` | `u256.Zero` | The value of the fee for flash loan |

#### Returns

`void`

#### Defined in

[assembly/interfaces/IFactory.ts:31](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IFactory.ts#L31)

___

### setPreset

▸ **setPreset**(`_binStep`, `_baseFactor`, `_filterPeriod`, `_decayPeriod`, `_reductionFactor`, `_variableFeeControl`, `_protocolShare`, `_maxVolatilityAccumulated`, `_sampleLifeTime`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `_binStep` | `u32` |
| `_baseFactor` | `u32` |
| `_filterPeriod` | `u32` |
| `_decayPeriod` | `u32` |
| `_reductionFactor` | `u32` |
| `_variableFeeControl` | `u32` |
| `_protocolShare` | `u32` |
| `_maxVolatilityAccumulated` | `u32` |
| `_sampleLifeTime` | `u32` |

#### Returns

`void`

#### Defined in

[assembly/interfaces/IFactory.ts:99](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IFactory.ts#L99)

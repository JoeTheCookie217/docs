# IPair

## Table of contents

### Constructors

- [constructor](IPair.md#constructor)

### Properties

- [\_origin](IPair.md#_origin)

### Methods

- [balanceOf](IPair.md#balanceof)
- [balanceOfBatch](IPair.md#balanceofbatch)
- [burn](IPair.md#burn)
- [collectFees](IPair.md#collectfees)
- [feeParameters](IPair.md#feeparameters)
- [findFirstNonEmptyBinId](IPair.md#findfirstnonemptybinid)
- [flashLoan](IPair.md#flashloan)
- [forceDecay](IPair.md#forcedecay)
- [getBin](IPair.md#getbin)
- [getFactory](IPair.md#getfactory)
- [getOracleParameters](IPair.md#getoracleparameters)
- [getOracleSampleFrom](IPair.md#getoraclesamplefrom)
- [getPairInformation](IPair.md#getpairinformation)
- [getTokenX](IPair.md#gettokenx)
- [getTokenY](IPair.md#gettokeny)
- [getUserBins](IPair.md#getuserbins)
- [increaseOracleLength](IPair.md#increaseoraclelength)
- [init](IPair.md#init)
- [isApprovedForAll](IPair.md#isapprovedforall)
- [mint](IPair.md#mint)
- [name](IPair.md#name)
- [pendingFees](IPair.md#pendingfees)
- [safeBatchTransferFrom](IPair.md#safebatchtransferfrom)
- [safeTransferFrom](IPair.md#safetransferfrom)
- [setApprovalForAll](IPair.md#setapprovalforall)
- [setFeesParameters](IPair.md#setfeesparameters)
- [swap](IPair.md#swap)
- [symbol](IPair.md#symbol)
- [totalSupply](IPair.md#totalsupply)

## Constructors

### constructor

• **new IPair**(`at`): [`IPair`](IPair.md)

Wraps a smart contract exposing standard token FFI.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `at` | `Address` | Address of the smart contract. |

#### Returns

[`IPair`](IPair.md)

#### Defined in

[assembly/interfaces/IPair.ts:30](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L30)

## Properties

### \_origin

• **\_origin**: `Address`

#### Defined in

[assembly/interfaces/IPair.ts:23](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L23)

## Methods

### balanceOf

▸ **balanceOf**(`_account`, `_id`): `u256`

#### Parameters

| Name | Type |
| :------ | :------ |
| `_account` | `Address` |
| `_id` | `u64` |

#### Returns

`u256`

#### Defined in

[assembly/interfaces/IPair.ts:244](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L244)

___

### balanceOfBatch

▸ **balanceOfBatch**(`_accounts`, `_ids`): `u256`[]

#### Parameters

| Name | Type |
| :------ | :------ |
| `_accounts` | `Address`[] |
| `_ids` | `u64`[] |

#### Returns

`u256`[]

#### Defined in

[assembly/interfaces/IPair.ts:254](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L254)

___

### burn

▸ **burn**(`_ids`, `_amounts`, `_to`, `masToSend`): `Amounts`

Burn LB tokens for each bins where the user removes liquidity.
This function will not transfer the LBToken from the caller, it is expected that the tokens have already been
transferred to this contract through another contract.
That is why this function shouldn't be called directly, but through one of the remove liquidity functions of the
router that will also perform safety checks.
The lengths of the arrays must be the same.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `_ids` | `u64`[] | The ids of the bins where the liquidity will be removed. It will burn LB tokens for each of these bins. |
| `_amounts` | `u256`[] | The amount of LB tokens to burn for each bin. |
| `_to` | `Address` | The address that will receive the tokens. |
| `masToSend` | `u64` | The amount of Massa to send for storage |

#### Returns

`Amounts`

- The amount of token X and token Y that the user will receive.

#### Defined in

[assembly/interfaces/IPair.ts:160](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L160)

___

### collectFees

▸ **collectFees**(`account`, `ids`, `masToSend`): `Amounts`

Collect the fees accumulated by a user.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `account` | `Address` | - |
| `ids` | `u64`[] | - |
| `masToSend` | `u64` | The amount of Massa to send for storage |

#### Returns

`Amounts`

amountX The amount of token X collected and sent to `_account`

amountY The amount of token Y collected and sent to `_account`

#### Defined in

[assembly/interfaces/IPair.ts:342](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L342)

___

### feeParameters

▸ **feeParameters**(): [`FeeParameters`](../structs/FeeParameters.md)

Get the fees parameters for this pair

#### Returns

[`FeeParameters`](../structs/FeeParameters.md)

#### Defined in

[assembly/interfaces/IPair.ts:72](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L72)

___

### findFirstNonEmptyBinId

▸ **findFirstNonEmptyBinId**(`id`, `sentTokenY`): `Result`<`u32`\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `id` | `u32` |
| `sentTokenY` | `bool` |

#### Returns

`Result`<`u32`\>

#### Defined in

[assembly/interfaces/IPair.ts:201](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L201)

___

### flashLoan

▸ **flashLoan**(`token`, `amount`, `masToSend`): `void`

Execute a flash loan.
The caller must implement the `IFlashLoanCallback` interface and have the `flashLoanCallback` function.
The `flashLoanCallback` function will be called by the pair contract to execute the logic of the flash loan.
The caller must return `true` if the flash loan was successful, and `false` otherwise.
The caller is expected to transfer the `amount + fee` of the token to this contract.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `token` | [`IERC20`](IERC20.md) | The token to flash loan |
| `amount` | `u256` | The amount of tokens to flash loan |
| `masToSend` | `u64` | The amount of Massa to send for storage |

#### Returns

`void`

#### Defined in

[assembly/interfaces/IPair.ts:178](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L178)

___

### forceDecay

▸ **forceDecay**(): `void`

#### Returns

`void`

#### Defined in

[assembly/interfaces/IPair.ts:225](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L225)

___

### getBin

▸ **getBin**(`_id`): [`Bin`](../structs/Bin.md)

Get the bin information for a given id

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `_id` | `u32` | The id of the bin |

#### Returns

[`Bin`](../structs/Bin.md)

#### Defined in

[assembly/interfaces/IPair.ts:83](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L83)

___

### getFactory

▸ **getFactory**(): `Address`

#### Returns

`Address`

#### Defined in

[assembly/interfaces/IPair.ts:216](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L216)

___

### getOracleParameters

▸ **getOracleParameters**(): [`OracleParameters`](../structs/OracleParameters.md)

#### Returns

[`OracleParameters`](../structs/OracleParameters.md)

#### Defined in

[assembly/interfaces/IPair.ts:348](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L348)

___

### getOracleSampleFrom

▸ **getOracleSampleFrom**(`timeDelta`): `OracleSampleReturn`

#### Parameters

| Name | Type |
| :------ | :------ |
| `timeDelta` | `u64` |

#### Returns

`OracleSampleReturn`

#### Defined in

[assembly/interfaces/IPair.ts:353](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L353)

___

### getPairInformation

▸ **getPairInformation**(): [`PairInformation`](../structs/PairInformation.md)

#### Returns

[`PairInformation`](../structs/PairInformation.md)

#### Defined in

[assembly/interfaces/IPair.ts:191](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L191)

___

### getTokenX

▸ **getTokenX**(): [`IERC20`](IERC20.md)

#### Returns

[`IERC20`](IERC20.md)

#### Defined in

[assembly/interfaces/IPair.ts:183](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L183)

___

### getTokenY

▸ **getTokenY**(): [`IERC20`](IERC20.md)

#### Returns

[`IERC20`](IERC20.md)

#### Defined in

[assembly/interfaces/IPair.ts:187](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L187)

___

### getUserBins

▸ **getUserBins**(`account`): `u32`[]

#### Parameters

| Name | Type |
| :------ | :------ |
| `account` | `Address` |

#### Returns

`u32`[]

#### Defined in

[assembly/interfaces/IPair.ts:196](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L196)

___

### increaseOracleLength

▸ **increaseOracleLength**(`newSize`, `masToSend`): `void`

Increases the length of the oracle to the given `_newLength` by adding empty samples to the end of the oracle.
The samples are however initialized to reduce the gas cost of the updates during a swap.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `newSize` | `u64` | - |
| `masToSend` | `u64` | The amount of Massa to send for storage |

#### Returns

`void`

#### Defined in

[assembly/interfaces/IPair.ts:370](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L370)

___

### init

▸ **init**(`factory`, `tokenX`, `tokenY`, `activeId`, `preset`, `masToSend`): `void`

Calls the constructor

#### Parameters

| Name | Type |
| :------ | :------ |
| `factory` | `Address` |
| `tokenX` | `Address` |
| `tokenY` | `Address` |
| `activeId` | `u32` |
| `preset` | [`Preset`](../structs/Preset.md) |
| `masToSend` | `u64` |

#### Returns

`void`

#### Defined in

[assembly/interfaces/IPair.ts:39](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L39)

___

### isApprovedForAll

▸ **isApprovedForAll**(`_owner`, `_spender`): `bool`

#### Parameters

| Name | Type |
| :------ | :------ |
| `_owner` | `Address` |
| `_spender` | `Address` |

#### Returns

`bool`

#### Defined in

[assembly/interfaces/IPair.ts:261](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L261)

___

### mint

▸ **mint**(`_ids`, `_distributionX`, `_distributionY`, `_to`, `masToSend`): `MintReturn`

Mint new LB tokens for each bins where the user adds liquidity.
This function will not transfer the tokens from the caller, it is expected that the tokens have already been
transferred to this contract through another contract.
That is why this function shouldn't be called directly, but through one of the add liquidity functions of the
router that will also perform safety checks.
Any excess amount of token will be sent to the `to` address. The lengths of the arrays must be the same.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `_ids` | `u64`[] | The ids of the bins where the liquidity will be added. It will mint LB tokens for each of these bins. |
| `_distributionX` | `u256`[] | The percentage of token X to add to each bin. The sum of all the values must not exceed 100%, that is 1e9. |
| `_distributionY` | `u256`[] | The percentage of token Y to add to each bin. The sum of all the values must not exceed 100%, that is 1e9. |
| `_to` | `Address` | The address that will receive the LB tokens and the excess amount of tokens. |
| `masToSend` | `u64` | The amount of Massa to send for storage. |

#### Returns

`MintReturn`

- The amount of token X and token Y that the user will receive and the amounts of LB tokens minted for each bin.

#### Defined in

[assembly/interfaces/IPair.ts:125](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L125)

___

### name

▸ **name**(): `string`

#### Returns

`string`

#### Defined in

[assembly/interfaces/IPair.ts:229](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L229)

___

### pendingFees

▸ **pendingFees**(`account`, `ids`): `Amounts`

#### Parameters

| Name | Type |
| :------ | :------ |
| `account` | `Address` |
| `ids` | `u64`[] |

#### Returns

`Amounts`

#### Defined in

[assembly/interfaces/IPair.ts:328](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L328)

___

### safeBatchTransferFrom

▸ **safeBatchTransferFrom**(`_from`, `_to`, `_ids`, `_amounts`, `masToSend`): `void`

Batch transfers `_amount` tokens of type `_id` from `_from` to `_to`

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `_from` | `Address` | The address of the owner of the tokens |
| `_to` | `Address` | The address of the recipient |
| `_ids` | `u64`[] | The list of token ids |
| `_amounts` | `u256`[] | The list of amounts to send |
| `masToSend` | `u64` | The amount of Massa to send for storage |

#### Returns

`void`

#### Defined in

[assembly/interfaces/IPair.ts:317](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L317)

___

### safeTransferFrom

▸ **safeTransferFrom**(`_from`, `_to`, `_id`, `amount`, `masToSend`): `void`

Transfers `_amount` token of type `_id` from `_from` to `_to`

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `_from` | `Address` | The address of the owner of the token |
| `_to` | `Address` | The address of the recipient |
| `_id` | `u64` | The token id |
| `amount` | `u256` | - |
| `masToSend` | `u64` | The amount of Massa to send for storage |

#### Returns

`void`

#### Defined in

[assembly/interfaces/IPair.ts:294](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L294)

___

### setApprovalForAll

▸ **setApprovalForAll**(`_approved`, `_sender`, `masToSend`): `void`

Grants or revokes permission to `spender` to transfer the caller's tokens, according to `approved`

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `_approved` | `bool` | The boolean value to grant or revoke permission |
| `_sender` | `Address` | - |
| `masToSend` | `u64` | The amount of Massa to send for storage |

#### Returns

`void`

#### Defined in

[assembly/interfaces/IPair.ts:277](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L277)

___

### setFeesParameters

▸ **setFeesParameters**(`fp`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `fp` | [`FeeParameters`](../structs/FeeParameters.md) |

#### Returns

`void`

#### Defined in

[assembly/interfaces/IPair.ts:220](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L220)

___

### swap

▸ **swap**(`swapForY`, `to`, `masToSend`): `u256`

Swap tokens iterating over the bins until the entire amount is swapped.
Will swap token X for token Y if `_swapForY` is true, and token Y for token X if `_swapForY` is false.
This function will not transfer the tokens from the caller, it is expected that the tokens have already been
transferred to this contract through another contract.
That is why this function shouldn't be called directly, but through one of the swap functions of the router
that will also perform safety checks.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `swapForY` | `bool` | Whether you've swapping token X for token Y (true) or token Y for token X (false) |
| `to` | `Address` | The address to send the tokens to |
| `masToSend` | `u64` | The amount of Massa to send for storage |

#### Returns

`u256`

#### Defined in

[assembly/interfaces/IPair.ts:101](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L101)

___

### symbol

▸ **symbol**(): `string`

#### Returns

`string`

#### Defined in

[assembly/interfaces/IPair.ts:234](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L234)

___

### totalSupply

▸ **totalSupply**(`_id`): `u256`

#### Parameters

| Name | Type |
| :------ | :------ |
| `_id` | `u64` |

#### Returns

`u256`

#### Defined in

[assembly/interfaces/IPair.ts:239](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/interfaces/IPair.ts#L239)

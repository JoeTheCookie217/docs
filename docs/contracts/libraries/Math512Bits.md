# Math512Bits

## Table of contents

### Constructors

- [constructor](Math512Bits.md#constructor)

### Methods

- [mulDivRoundDown](Math512Bits.md#muldivrounddown)
- [mulShiftRoundDown](Math512Bits.md#mulshiftrounddown)
- [mulShiftRoundUp](Math512Bits.md#mulshiftroundup)
- [shiftDivRoundDown](Math512Bits.md#shiftdivrounddown)
- [shiftDivRoundUp](Math512Bits.md#shiftdivroundup)

## Constructors

### constructor

• **new Math512Bits**(): [`Math512Bits`](Math512Bits.md)

#### Returns

[`Math512Bits`](Math512Bits.md)

## Methods

### mulDivRoundDown

▸ **mulDivRoundDown**(`x`, `y`, `denominator`): `u256`

Calculates floor(x*y÷denominator) with full precision
The result will be rounded down

Credit to Remco Bloemen under MIT license https://xn--2-umb.com/21/muldiv

Requirements:
- The denominator cannot be zero
- The result must fit within u256

Caveats:
- This function does not work with fixed-point numbers

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `x` | `u256` | The multiplicand as an u256 |
| `y` | `u256` | The multiplier as an u256 |
| `denominator` | `u256` | The divisor as an u256 |

#### Returns

`u256`

The result as an u256

#### Defined in

[assembly/libraries/Math512Bits.ts:29](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/libraries/Math512Bits.ts#L29)

___

### mulShiftRoundDown

▸ **mulShiftRoundDown**(`x`, `y`, `offset`): `u256`

Calculates x * y >> offset with full precision
The result will be rounded down

Credit to Remco Bloemen under MIT license https://xn--2-umb.com/21/muldiv

Requirements:
- The offset needs to be strictly lower than 256
- The result must fit within u256

Caveats:
- This function does not work with fixed-point numbers

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `x` | `u256` | The multiplicand as an u256 |
| `y` | `u256` | The multiplier as an u256 |
| `offset` | `i32` | The offset, can't be greater than 255 |

#### Returns

`u256`

The result as an u256

#### Defined in

[assembly/libraries/Math512Bits.ts:86](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/libraries/Math512Bits.ts#L86)

___

### mulShiftRoundUp

▸ **mulShiftRoundUp**(`x`, `y`, `offset`): `u256`

Calculates x * y >> offset with full precision
The result will be rounded up

Credit to Remco Bloemen under MIT license https://xn--2-umb.com/21/muldiv

Requirements:
- The offset needs to be strictly lower than 128
- The result must fit within u256

Caveats:
- This function does not work with fixed-point numbers

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `x` | `u256` | The multiplicand as an u256 |
| `y` | `u256` | The multiplier as an u256 |
| `offset` | `i32` | The offset, can't be greater than 128 |

#### Returns

`u256`

The result as an u256

#### Defined in

[assembly/libraries/Math512Bits.ts:150](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/libraries/Math512Bits.ts#L150)

___

### shiftDivRoundDown

▸ **shiftDivRoundDown**(`x`, `offset`, `denominator`): `u256`

Calculates x << offset / y with full precision
The result will be rounded down

Credit to Remco Bloemen under MIT license https://xn--2-umb.com/21/muldiv

Requirements:
- The offset needs to be strictly lower than 256
- The result must fit within u256

Caveats:
- This function does not work with fixed-point numbers

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `x` | `u256` | The multiplicand as an u256 |
| `offset` | `i32` | The number of bit to shift x |
| `denominator` | `u256` | The divisor as an u256 |

#### Returns

`u256`

The result as an u256

#### Defined in

[assembly/libraries/Math512Bits.ts:53](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/libraries/Math512Bits.ts#L53)

___

### shiftDivRoundUp

▸ **shiftDivRoundUp**(`x`, `offset`, `denominator`): `u256`

Calculates x << offset / y with full precision
The result will be rounded up

Credit to Remco Bloemen under MIT license https://xn--2-umb.com/21/muldiv

Requirements:
- The offset needs to be strictly lower than 128
- The result must fit within u256

Caveats:
- This function does not work with fixed-point numbers

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `x` | `u256` | The multiplicand as an u256 |
| `offset` | `i32` | The number of bit to shift x |
| `denominator` | `u256` | The divisor as an u256 |

#### Returns

`u256`

The result as an u256

#### Defined in

[assembly/libraries/Math512Bits.ts:124](https://github.com/dusaprotocol/v1-core-confidencial/blob/b44ea92/assembly/libraries/Math512Bits.ts#L124)

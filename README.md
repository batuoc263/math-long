# Math long

A Long class for representing a 64 bit two's-complement integer value derived from the Closure Library for stand-alone use and extended with unsigned support.

Build Status Publish Status npm

## Background
As of ECMA-262 5th Edition, "all the positive and negative integers whose magnitude is no greater than 253 are representable in the Number type", which is "representing the doubleprecision 64-bit format IEEE 754 values as specified in the IEEE Standard for Binary Floating-Point Arithmetic". The maximum safe integer in JavaScript is 253-1.

Example: 264-1 is 18446744073709551615 but in JavaScript it evaluates to 18446744073709552000.

Furthermore, bitwise operators in JavaScript "deal only with integers in the range −231 through 231−1, inclusive, or in the range 0 through 232−1, inclusive. These operators accept any value of the Number type but first convert each such value to one of 232 integer values."

In some use cases, however, it is required to be able to reliably work with and perform bitwise operations on the full 64 bits. This is where math-long comes into play.

## Usage
The package exports an ECMAScript module with an UMD fallback.

```shell
npm install math-long
```

```js
import Long from "long";

var value = new Long(0xFFFFFFFF, 0x7FFFFFFF);
console.log(value.toString());
...
```

Note that mixing ESM and CommonJS is not recommended as it yields different classes, albeit with the same functionality.

# API
## Constructor
new Long(low: number, high?: number, unsigned?: boolean)
Constructs a 64 bit two's-complement integer, given its low and high 32 bit values as signed integers. See the from* functions below for more convenient ways of constructing Longs.

## Fields
Long#low: number
The low 32 bits as a signed value.

Long#high: number
The high 32 bits as a signed value.

Long#unsigned: boolean
Whether unsigned or not.

## Constants
Long.ZERO: Long
Signed zero.

Long.ONE: Long
Signed one.

Long.NEG_ONE: Long
Signed negative one.

Long.UZERO: Long
Unsigned zero.

Long.UONE: Long
Unsigned one.

Long.MAX_VALUE: Long
Maximum signed value.

Long.MIN_VALUE: Long
Minimum signed value.

Long.MAX_UNSIGNED_VALUE: Long
Maximum unsigned value.

## Utility
Long.isLong(obj: *): boolean
Tests if the specified object is a Long.

Long.fromBits(lowBits: number, highBits: number, unsigned?: boolean): Long
Returns a Long representing the 64 bit integer that comes by concatenating the given low and high bits. Each is assumed to use 32 bits.

Long.fromBytes(bytes: number[], unsigned?: boolean, le?: boolean): Long
Creates a Long from its byte representation.

Long.fromBytesLE(bytes: number[], unsigned?: boolean): Long
Creates a Long from its little endian byte representation.

Long.fromBytesBE(bytes: number[], unsigned?: boolean): Long
Creates a Long from its big endian byte representation.

Long.fromInt(value: number, unsigned?: boolean): Long
Returns a Long representing the given 32 bit integer value.

Long.fromNumber(value: number, unsigned?: boolean): Long
Returns a Long representing the given value, provided that it is a finite number. Otherwise, zero is returned.

Long.fromString(str: string, unsigned?: boolean, radix?: number)
Long.fromString(str: string, radix: number)
Returns a Long representation of the given string, written using the specified radix.

Long.fromValue(val: *, unsigned?: boolean): Long
Converts the specified value to a Long using the appropriate from* function for its type.

## Methods
Long#add(addend: Long | number | string): Long
Returns the sum of this and the specified Long.

Long#and(other: Long | number | string): Long
Returns the bitwise AND of this Long and the specified.

Long#compare/comp(other: Long | number | string): number
Compares this Long's value with the specified's. Returns 0 if they are the same, 1 if the this is greater and -1 if the given one is greater.

Long#divide/div(divisor: Long | number | string): Long
Returns this Long divided by the specified.

Long#equals/eq(other: Long | number | string): boolean
Tests if this Long's value equals the specified's.

Long#getHighBits(): number
Gets the high 32 bits as a signed integer.

Long#getHighBitsUnsigned(): number
Gets the high 32 bits as an unsigned integer.

Long#getLowBits(): number
Gets the low 32 bits as a signed integer.

Long#getLowBitsUnsigned(): number
Gets the low 32 bits as an unsigned integer.

Long#getNumBitsAbs(): number
Gets the number of bits needed to represent the absolute value of this Long.

Long#greaterThan/gt(other: Long | number | string): boolean
Tests if this Long's value is greater than the specified's.

Long#greaterThanOrEqual/gte/ge(other: Long | number | string): boolean
Tests if this Long's value is greater than or equal the specified's.

Long#isEven(): boolean
Tests if this Long's value is even.

Long#isNegative(): boolean
Tests if this Long's value is negative.

Long#isOdd(): boolean
Tests if this Long's value is odd.

Long#isPositive(): boolean
Tests if this Long's value is positive or zero.

Long#isZero/eqz(): boolean
Tests if this Long's value equals zero.

Long#lessThan/lt(other: Long | number | string): boolean
Tests if this Long's value is less than the specified's.

Long#lessThanOrEqual/lte/le(other: Long | number | string): boolean
Tests if this Long's value is less than or equal the specified's.

Long#modulo/mod/rem(divisor: Long | number | string): Long
Returns this Long modulo the specified.

Long#multiply/mul(multiplier: Long | number | string): Long
Returns the product of this and the specified Long.

Long#negate/neg(): Long
Negates this Long's value.

Long#not(): Long
Returns the bitwise NOT of this Long.

Long#countLeadingZeros/clz(): number
Returns count leading zeros of this Long.

Long#countTrailingZeros/ctz(): number
Returns count trailing zeros of this Long.

Long#notEquals/neq/ne(other: Long | number | string): boolean
Tests if this Long's value differs from the specified's.

Long#or(other: Long | number | string): Long
Returns the bitwise OR of this Long and the specified.

Long#shiftLeft/shl(numBits: Long | number | string): Long
Returns this Long with bits shifted to the left by the given amount.

Long#shiftRight/shr(numBits: Long | number | string): Long
Returns this Long with bits arithmetically shifted to the right by the given amount.

Long#shiftRightUnsigned/shru/shr_u(numBits: Long | number | string): Long
Returns this Long with bits logically shifted to the right by the given amount.

Long#rotateLeft/rotl(numBits: Long | number | string): Long
Returns this Long with bits rotated to the left by the given amount.

Long#rotateRight/rotr(numBits: Long | number | string): Long
Returns this Long with bits rotated to the right by the given amount.

Long#subtract/sub(subtrahend: Long | number | string): Long
Returns the difference of this and the specified Long.

Long#toBytes(le?: boolean): number[]
Converts this Long to its byte representation.

Long#toBytesLE(): number[]
Converts this Long to its little endian byte representation.

Long#toBytesBE(): number[]
Converts this Long to its big endian byte representation.

Long#toInt(): number
Converts the Long to a 32 bit integer, assuming it is a 32 bit integer.

Long#toNumber(): number
Converts the Long to a the nearest floating-point representation of this value (double, 53 bit mantissa).

Long#toSigned(): Long
Converts this Long to signed.

Long#toString(radix?: number): string
Converts the Long to a string written in the specified radix.

Long#toUnsigned(): Long
Converts this Long to unsigned.

Long#xor(other: Long | number | string): Long
Returns the bitwise XOR of this Long and the given one.
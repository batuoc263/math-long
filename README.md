# Math long

A Long class for representing a 64 bit two's-complement integer value derived from the Closure Library for stand-alone use and extended with unsigned support.

Build Status Publish Status npm

## Background
As of ECMA-262 5th Edition, "all the positive and negative integers whose magnitude is no greater than 253 are representable in the Number type", which is "representing the doubleprecision 64-bit format IEEE 754 values as specified in the IEEE Standard for Binary Floating-Point Arithmetic". The maximum safe integer in JavaScript is 253-1.

Example: 264-1 is 18446744073709551615 but in JavaScript it evaluates to 18446744073709552000.

Furthermore, bitwise operators in JavaScript "deal only with integers in the range −231 through 231−1, inclusive, or in the range 0 through 232−1, inclusive. These operators accept any value of the Number type but first convert each such value to one of 232 integer values."

In some use cases, however, it is required to be able to reliably work with and perform bitwise operations on the full 64 bits. This is where long.js comes into play.

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
# BSON
### `function calculateObjectSize(object: Document, options: CalculateObjectSizeOptions): number`
Calculate the bson size for a passed in Javascript object.

- `@param` `object` - the Javascript object to calculate the BSON byte size for

- `@return` size of BSON object in bytes


### `function deserialize(buffer: Buffer | ArrayBufferView | ArrayBuffer, options: DeserializeOptions): Document`
Deserialize data as BSON.

- `@param` `buffer` - the buffer containing the serialized set of BSON documents.

- `@return` returns the deserialized Javascript Object.


### `function deserializeStream(data: Buffer | ArrayBufferView | ArrayBuffer, startIndex: number, numberOfDocuments: number, documents: Document[], docStartIndex: number, options: DeserializeOptions): number`
Deserialize stream data as BSON documents.

- `@param` `data` - the buffer containing the serialized set of BSON documents.

- `@param` `startIndex` - the start index in the data Buffer where the deserialization is to start.

- `@param` `numberOfDocuments` - number of documents to deserialize.

- `@param` `documents` - an array where to store the deserialized documents.

- `@param` `docStartIndex` - the index in the documents array from where to start inserting documents.

- `@param` `options` - additional options used for the deserialization.

- `@return` next index in the buffer after deserialization **x** numbers of documents.


### `function serialize(object: Document, options: SerializeOptions): Buffer`
Serialize a Javascript object.

- `@param` `object` - the Javascript object to serialize.

- `@return` Buffer object containing the serialized object.


### `function serializeWithBufferAndIndex(object: Document, finalBuffer: Buffer, options: SerializeOptions): number`
Serialize a Javascript object using a predefined Buffer and index into the buffer,
useful when pre-allocating the space for serialization.

- `@param` `object` - the Javascript object to serialize.

- `@param` `finalBuffer` - the Buffer you pre-allocated to store the serialized BSON object.

- `@return` the index pointing to the last written byte in the buffer.


### `function setInternalBufferSize(size: number): void`
Sets the size of the internal serialization buffer.

- `@param` `size` - The desired size for the internal serialization buffer


### const LongWithoutOverridesClass: LongWithoutOverrides


### let Map: MapConstructor


### const default
BSON default export

@deprecated
 Please use named exports

@private

### class BSONError extends Error


constructor(message: string)
get name(): string

### class BSONRegExp
A class representation of the BSON RegExp type.


constructor(pattern: string, options?: string)

- `@param` `pattern` - The regular expression pattern to match

- `@param` `options` - The regular expression options

- `_bsontype: "BSONRegExp"` 
- `pattern: string` 
- `options: string` 
static parseOptions(options?: string): string
toExtendedJSON(options?: EJSONOptions): BSONRegExpExtendedLegacy | BSONRegExpExtended

static fromExtendedJSON(doc: BSONRegExpExtendedLegacy | BSONRegExpExtended): BSONRegExp


### class BSONSymbol
A class representation of the BSON Symbol type.


constructor(value: string)

- `@param` `value` - the string representing the symbol.

- `_bsontype: "Symbol"` 
- `value: string` 
valueOf(): string
Access the wrapped string value.
toString(): string
inspect(): string

toJSON(): string
toExtendedJSON(): BSONSymbolExtended

static fromExtendedJSON(doc: BSONSymbolExtended): BSONSymbol

[Symbol.for('nodejs.util.inspect.custom')](): string


### class BSONTypeError extends TypeError


constructor(message: string)
get name(): string

### class Binary
A class representation of the BSON Binary type.


constructor(buffer?: string | BinarySequence, subType?: number)

- `@param` `buffer` - a buffer object containing the binary data.

- `@param` `subType` - the option binary type.

- `_bsontype: "Binary"` 
- `static readonly BUFFER_SIZE` 
Initial buffer default size
- `static readonly SUBTYPE_DEFAULT` 
Default BSON type
- `static readonly SUBTYPE_FUNCTION` 
Function BSON type
- `static readonly SUBTYPE_BYTE_ARRAY` 
Byte Array BSON type
- `static readonly SUBTYPE_UUID_OLD` 
Deprecated UUID BSON type @deprecated Please use SUBTYPE_UUID
- `static readonly SUBTYPE_UUID` 
UUID BSON type
- `static readonly SUBTYPE_MD5` 
MD5 BSON type
- `static readonly SUBTYPE_ENCRYPTED` 
Encrypted BSON type
- `static readonly SUBTYPE_COLUMN` 
Column BSON type
- `static readonly SUBTYPE_USER_DEFINED` 
User BSON type
- `buffer: Buffer` 
- `sub_type: number` 
- `position: number` 
put(byteValue: string | number | Uint8Array | Buffer | number[]): void
Updates this binary with byte_value.

- `@param` `byteValue` - a single byte we wish to write.

write(sequence: string | BinarySequence, offset: number): void
Writes a buffer or string to the binary.

- `@param` `sequence` - a string or buffer to be written to the Binary BSON object.

- `@param` `offset` - specify the binary of where to write the content.

read(position: number, length: number): BinarySequence
Reads **length** bytes starting at **position**.

- `@param` `position` - read from the given position in the Binary.

- `@param` `length` - the number of bytes to read.

value(asRaw?: boolean): string | BinarySequence
Returns the value of this binary as a string.

- `@param` `asRaw` - Will skip converting to a string

> Note: This is handy when calling this function conditionally for some key value pairs and not others

length(): number
the length of the binary sequence
toJSON(): string
toString(format?: string): string
toExtendedJSON(options?: EJSONOptions): BinaryExtendedLegacy | BinaryExtended

toUUID(): UUID
static fromExtendedJSON(doc: BinaryExtendedLegacy | BinaryExtended | UUIDExtended, options?: EJSONOptions): Binary

[Symbol.for('nodejs.util.inspect.custom')](): string

inspect(): string

### class Code
A class representation of the BSON Code type.


constructor(code: string | Function, scope?: Document)

- `@param` `code` - a string or function.

- `@param` `scope` - an optional scope for the function.

- `_bsontype: "Code"` 
- `code: string | Function` 
- `scope?: Document` 
toJSON(): { code: string | Function; scope: Document; }
toExtendedJSON(): CodeExtended

static fromExtendedJSON(doc: CodeExtended): Code

[Symbol.for('nodejs.util.inspect.custom')](): string

inspect(): string

### class DBRef
A class representation of the BSON DBRef type.


constructor(collection: string, oid: ObjectId, db?: string, fields?: Document)

- `@param` `collection` - the collection name.

- `@param` `oid` - the reference ObjectId.

- `@param` `db` - optional db name, if omitted the reference is local to the current db.

- `_bsontype: "DBRef"` 
- `collection: string` 
- `oid: ObjectId` 
- `db?: string` 
- `fields: Document` 
get namespace(): string

set namespace(value: string)
toJSON(): DBRefLike & Document
toExtendedJSON(options?: EJSONOptions): DBRefLike

static fromExtendedJSON(doc: DBRefLike): DBRef

[Symbol.for('nodejs.util.inspect.custom')](): string

inspect(): string

### class Decimal128
A class representation of the BSON Decimal128 type.


constructor(bytes: Buffer | string)

- `@param` `bytes` - a buffer containing the raw Decimal128 bytes in little endian order,
 or a string representation as returned by .toString()

- `_bsontype: "Decimal128"` 
- `readonly bytes: Buffer` 
static fromString(representation: string): Decimal128
Create a Decimal128 instance from a string representation

- `@param` `representation` - a numeric string representation.

toString(): string
Create a string representation of the raw Decimal128 value
toJSON(): Decimal128Extended
toExtendedJSON(): Decimal128Extended

static fromExtendedJSON(doc: Decimal128Extended): Decimal128

[Symbol.for('nodejs.util.inspect.custom')](): string

inspect(): string

### class Double
A class representation of the BSON Double type.


constructor(value: number)
Create a Double type

- `@param` `value` - the number we want to represent as a double.

- `_bsontype: "Double"` 
- `value: number` 
valueOf(): number
Access the number value.

- `@return` returns the wrapped double number.

toJSON(): number
toString(radix?: number): string
toExtendedJSON(options?: EJSONOptions): number | DoubleExtended

static fromExtendedJSON(doc: DoubleExtended, options?: EJSONOptions): number | Double

[Symbol.for('nodejs.util.inspect.custom')](): string

inspect(): string

### class Int32
A class representation of a BSON Int32 type.


constructor(value: number | string)
Create an Int32 type

- `@param` `value` - the number we want to represent as an int32.

- `_bsontype: "Int32"` 
- `value: number` 
valueOf(): number
Access the number value.

- `@return` returns the wrapped int32 number.

toString(radix?: number): string
toJSON(): number
toExtendedJSON(options?: EJSONOptions): number | Int32Extended

static fromExtendedJSON(doc: Int32Extended, options?: EJSONOptions): number | Int32

[Symbol.for('nodejs.util.inspect.custom')](): string

inspect(): string

### class Long
A class representing a 64-bit integer

> Note: The internal representation of a long is the two given signed, 32-bit values.
We use 32-bit pieces because these are the size of integers on which
Javascript performs bit-operations.  For operations like addition and
multiplication, we split each number into 16 bit pieces, which can easily be
multiplied within Javascript's floating-point representation without overflow
or change in sign.
In the algorithms below, we frequently reduce the negative case to the
positive case by negating the input(s) and then post-processing the result.
Note that we must ALWAYS check specially whether those values are MIN_VALUE
(-2^63) because -MIN_VALUE == MIN_VALUE (since 2^63 cannot be represented as
a positive number, it overflows back into a negative).  Not handling this
case would often result in infinite recursion.
Common constant values ZERO, ONE, NEG_ONE, etc. are found as static properties on this class.


constructor(low: number | bigint | string, high?: number | boolean, unsigned?: boolean)
Constructs a 64 bit two's-complement integer, given its low and high 32 bit values as *signed* integers.
 See the from* functions below for more convenient ways of constructing Longs.

Acceptable signatures are:
- Long(low, high, unsigned?)
- Long(bigint, unsigned?)
- Long(string, unsigned?)

- `@param` `low` - The low (signed) 32 bits of the long

- `@param` `high` - The high (signed) 32 bits of the long

- `@param` `unsigned` - Whether unsigned or not, defaults to signed

- `_bsontype: "Long"` 
- `__isLong__: true` 
An indicator used to reliably determine if an object is a Long or not.
- `high: number` 
The high 32 bits as a signed value.
- `low: number` 
The low 32 bits as a signed value.
- `unsigned: boolean` 
Whether unsigned or not.
- `static TWO_PWR_24` 
- `static MAX_UNSIGNED_VALUE` 
Maximum unsigned value.
- `static ZERO` 
Signed zero
- `static UZERO` 
Unsigned zero.
- `static ONE` 
Signed one.
- `static UONE` 
Unsigned one.
- `static NEG_ONE` 
Signed negative one.
- `static MAX_VALUE` 
Maximum signed value.
- `static MIN_VALUE` 
Minimum signed value.
static fromBits(lowBits: number, highBits: number, unsigned?: boolean): Long
Returns a Long representing the 64 bit integer that comes by concatenating the given low and high bits.
Each is assumed to use 32 bits.

- `@param` `lowBits` - The low 32 bits

- `@param` `highBits` - The high 32 bits

- `@param` `unsigned` - Whether unsigned or not, defaults to signed

- `@return` The corresponding Long value

static fromInt(value: number, unsigned?: boolean): Long
Returns a Long representing the given 32 bit integer value.

- `@param` `value` - The 32 bit integer in question

- `@param` `unsigned` - Whether unsigned or not, defaults to signed

- `@return` The corresponding Long value

static fromNumber(value: number, unsigned?: boolean): Long
Returns a Long representing the given value, provided that it is a finite number. Otherwise, zero is returned.

- `@param` `value` - The number in question

- `@param` `unsigned` - Whether unsigned or not, defaults to signed

- `@return` The corresponding Long value

static fromBigInt(value: bigint, unsigned?: boolean): Long
Returns a Long representing the given value, provided that it is a finite number. Otherwise, zero is returned.

- `@param` `value` - The number in question

- `@param` `unsigned` - Whether unsigned or not, defaults to signed

- `@return` The corresponding Long value

static fromString(str: string, unsigned?: boolean, radix?: number): Long
Returns a Long representation of the given string, written using the specified radix.

- `@param` `str` - The textual representation of the Long

- `@param` `unsigned` - Whether unsigned or not, defaults to signed

- `@param` `radix` - The radix in which the text is written (2-36), defaults to 10

- `@return` The corresponding Long value

static fromBytes(bytes: number[], unsigned?: boolean, le?: boolean): Long
Creates a Long from its byte representation.

- `@param` `bytes` - Byte representation

- `@param` `unsigned` - Whether unsigned or not, defaults to signed

- `@param` `le` - Whether little or big endian, defaults to big endian

- `@return` The corresponding Long value

static fromBytesLE(bytes: number[], unsigned?: boolean): Long
Creates a Long from its little endian byte representation.

- `@param` `bytes` - Little endian byte representation

- `@param` `unsigned` - Whether unsigned or not, defaults to signed

- `@return` The corresponding Long value

static fromBytesBE(bytes: number[], unsigned?: boolean): Long
Creates a Long from its big endian byte representation.

- `@param` `bytes` - Big endian byte representation

- `@param` `unsigned` - Whether unsigned or not, defaults to signed

- `@return` The corresponding Long value

static isLong(value: any): value is Long
Tests if the specified object is a Long.
static fromValue(val: number | string | { low: number; high: number; unsigned: boolean; }, unsigned?: boolean): Long
Converts the specified value to a Long.

- `@param` `unsigned` - Whether unsigned or not, defaults to signed

add(addend: string | number | Long | Timestamp): Long
Returns the sum of this and the specified Long.
and(other: string | number | Long | Timestamp): Long
Returns the sum of this and the specified Long.

- `@return` Sum

compare(other: string | number | Long | Timestamp): 0 | 1 | -1
Compares this Long's value with the specified's.

- `@return` 0 if they are the same, 1 if the this is greater and -1 if the given one is greater

comp(other: string | number | Long | Timestamp): 0 | 1 | -1
This is an alias of {@link Long.compare}
divide(divisor: string | number | Long | Timestamp): Long
Returns this Long divided by the specified. The result is signed if this Long is signed or unsigned if this Long is unsigned.

- `@return` Quotient

div(divisor: string | number | Long | Timestamp): Long
This is an alias of {@link Long.divide}
equals(other: string | number | Long | Timestamp): boolean
Tests if this Long's value equals the specified's.

- `@param` `other` - Other value

eq(other: string | number | Long | Timestamp): boolean
This is an alias of {@link Long.equals}
getHighBits(): number
Gets the high 32 bits as a signed integer.
getHighBitsUnsigned(): number
Gets the high 32 bits as an unsigned integer.
getLowBits(): number
Gets the low 32 bits as a signed integer.
getLowBitsUnsigned(): number
Gets the low 32 bits as an unsigned integer.
getNumBitsAbs(): number
Gets the number of bits needed to represent the absolute value of this Long.
greaterThan(other: string | number | Long | Timestamp): boolean
Tests if this Long's value is greater than the specified's.
gt(other: string | number | Long | Timestamp): boolean
This is an alias of {@link Long.greaterThan}
greaterThanOrEqual(other: string | number | Long | Timestamp): boolean
Tests if this Long's value is greater than or equal the specified's.
gte(other: string | number | Long | Timestamp): boolean
This is an alias of {@link Long.greaterThanOrEqual}
ge(other: string | number | Long | Timestamp): boolean
This is an alias of {@link Long.greaterThanOrEqual}
isEven(): boolean
Tests if this Long's value is even.
isNegative(): boolean
Tests if this Long's value is negative.
isOdd(): boolean
Tests if this Long's value is odd.
isPositive(): boolean
Tests if this Long's value is positive.
isZero(): boolean
Tests if this Long's value equals zero.
lessThan(other: string | number | Long | Timestamp): boolean
Tests if this Long's value is less than the specified's.
lt(other: string | number | Long | Timestamp): boolean
This is an alias of {@link Long#lessThan}.
lessThanOrEqual(other: string | number | Long | Timestamp): boolean
Tests if this Long's value is less than or equal the specified's.
lte(other: string | number | Long | Timestamp): boolean
This is an alias of {@link Long.lessThanOrEqual}
modulo(divisor: string | number | Long | Timestamp): Long
Returns this Long modulo the specified.
mod(divisor: string | number | Long | Timestamp): Long
This is an alias of {@link Long.modulo}
rem(divisor: string | number | Long | Timestamp): Long
This is an alias of {@link Long.modulo}
multiply(multiplier: string | number | Long | Timestamp): Long
Returns the product of this and the specified Long.

- `@param` `multiplier` - Multiplier

- `@return` Product

mul(multiplier: string | number | Long | Timestamp): Long
This is an alias of {@link Long.multiply}
negate(): Long
Returns the Negation of this Long's value.
neg(): Long
This is an alias of {@link Long.negate}
not(): Long
Returns the bitwise NOT of this Long.
notEquals(other: string | number | Long | Timestamp): boolean
Tests if this Long's value differs from the specified's.
neq(other: string | number | Long | Timestamp): boolean
This is an alias of {@link Long.notEquals}
ne(other: string | number | Long | Timestamp): boolean
This is an alias of {@link Long.notEquals}
or(other: number | string | Long): Long
Returns the bitwise OR of this Long and the specified.
shiftLeft(numBits: number | Long): Long
Returns this Long with bits shifted to the left by the given amount.

- `@param` `numBits` - Number of bits

- `@return` Shifted Long

shl(numBits: number | Long): Long
This is an alias of {@link Long.shiftLeft}
shiftRight(numBits: number | Long): Long
Returns this Long with bits arithmetically shifted to the right by the given amount.

- `@param` `numBits` - Number of bits

- `@return` Shifted Long

shr(numBits: number | Long): Long
This is an alias of {@link Long.shiftRight}
shiftRightUnsigned(numBits: Long | number): Long
Returns this Long with bits logically shifted to the right by the given amount.

- `@param` `numBits` - Number of bits

- `@return` Shifted Long

shr_u(numBits: number | Long): Long
This is an alias of {@link Long.shiftRightUnsigned}
shru(numBits: number | Long): Long
This is an alias of {@link Long.shiftRightUnsigned}
subtract(subtrahend: string | number | Long | Timestamp): Long
Returns the difference of this and the specified Long.

- `@param` `subtrahend` - Subtrahend

- `@return` Difference

sub(subtrahend: string | number | Long | Timestamp): Long
This is an alias of {@link Long.subtract}
toInt(): number
Converts the Long to a 32 bit integer, assuming it is a 32 bit integer.
toNumber(): number
Converts the Long to a the nearest floating-point representation of this value (double, 53 bit mantissa).
toBigInt(): bigint
Converts the Long to a BigInt (arbitrary precision).
toBytes(le?: boolean): number[]
Converts this Long to its byte representation.

- `@param` `le` - Whether little or big endian, defaults to big endian

- `@return` Byte representation

toBytesLE(): number[]
Converts this Long to its little endian byte representation.

- `@return` Little endian byte representation

toBytesBE(): number[]
Converts this Long to its big endian byte representation.

- `@return` Big endian byte representation

toSigned(): Long
Converts this Long to signed.
toString(radix?: number): string
Converts the Long to a string written in the specified radix.

- `@param` `radix` - Radix (2-36), defaults to 10

@@throws RangeError If `radix` is out of range
toUnsigned(): Long
Converts this Long to unsigned.
xor(other: Long | number | string): Long
Returns the bitwise XOR of this Long and the given one.
eqz(): boolean
This is an alias of {@link Long.isZero}
le(other: string | number | Long | Timestamp): boolean
This is an alias of {@link Long.lessThanOrEqual}
toExtendedJSON(options?: EJSONOptions): number | LongExtended
static fromExtendedJSON(doc: { $numberLong: string; }, options?: EJSONOptions): number | Long
[Symbol.for('nodejs.util.inspect.custom')](): string

inspect(): string

### class MaxKey
A class representation of the BSON MaxKey type.


constructor()
- `_bsontype: "MaxKey"` 
toExtendedJSON(): MaxKeyExtended

static fromExtendedJSON(): MaxKey

[Symbol.for('nodejs.util.inspect.custom')](): string

inspect(): string

### class MinKey
A class representation of the BSON MinKey type.


constructor()
- `_bsontype: "MinKey"` 
toExtendedJSON(): MinKeyExtended

static fromExtendedJSON(): MinKey

[Symbol.for('nodejs.util.inspect.custom')](): string

inspect(): string

### class ObjectID
A class representation of the BSON ObjectId type.


constructor(inputId?: string | number | ObjectId | ObjectIdLike | Buffer | Uint8Array)
Create an ObjectId type

- `@param` `inputId` - Can be a 24 character hex string, 12 byte binary Buffer, or a number.

- `_bsontype: "ObjectId"` 
- `static index` 

- `static cacheHexString: boolean` 
- `private [kId]: Buffer` 
ObjectId Bytes @internal
- `private __id?: string` 
ObjectId hexString cache @internal
get id(): Buffer
The ObjectId bytes

@readonly
set id(value: Buffer)
get generationTime(): number
The generation time of this ObjectId instance

@deprecated
 Please use getTimestamp / createFromTime which returns an int32 epoch

set generationTime(value: number)
toHexString(): string
Returns the ObjectId id as a 24 character hex string representation
static getInc(): number
Update the ObjectId index

@private
static generate(time?: number): Buffer
Generate a 12 byte id buffer used in ObjectId's

- `@param` `time` - pass in a second based timestamp.

toString(format?: string): string
Converts the id into a 24 character hex string for printing

- `@param` `format` - The Buffer toString format parameter.

toJSON(): string
Converts to its JSON the 24 character hex string representation.
equals(otherId: string | ObjectId | ObjectIdLike): boolean
Compares the equality of this ObjectId with `otherID`.

- `@param` `otherId` - ObjectId instance to compare against.

getTimestamp(): Date
Returns the generation date (accurate up to the second) that this ID was generated.
static createPk(): ObjectId

static createFromTime(time: number): ObjectId
Creates an ObjectId from a second based number, with the rest of the ObjectId zeroed out. Used for comparisons or sorting the ObjectId.

- `@param` `time` - an integer number representing a number of seconds.

static createFromHexString(hexString: string): ObjectId
Creates an ObjectId from a hex string representation of an ObjectId.

- `@param` `hexString` - create a ObjectId from a passed in 24 character hexstring.

static isValid(id: string | number | ObjectId | ObjectIdLike | Buffer | Uint8Array): boolean
Checks if a value is a valid bson ObjectId

- `@param` `id` - ObjectId instance to validate.

toExtendedJSON(): ObjectIdExtended

static fromExtendedJSON(doc: ObjectIdExtended): ObjectId

[Symbol.for('nodejs.util.inspect.custom')](): string
Converts to a string representation of this Id.

- `@return` return the 24 character hex string representation.

inspect(): string

### class ObjectId
A class representation of the BSON ObjectId type.


constructor(inputId?: string | number | ObjectId | ObjectIdLike | Buffer | Uint8Array)
Create an ObjectId type

- `@param` `inputId` - Can be a 24 character hex string, 12 byte binary Buffer, or a number.

- `_bsontype: "ObjectId"` 
- `static index` 

- `static cacheHexString: boolean` 
- `private [kId]: Buffer` 
ObjectId Bytes @internal
- `private __id?: string` 
ObjectId hexString cache @internal
get id(): Buffer
The ObjectId bytes

@readonly
set id(value: Buffer)
get generationTime(): number
The generation time of this ObjectId instance

@deprecated
 Please use getTimestamp / createFromTime which returns an int32 epoch

set generationTime(value: number)
toHexString(): string
Returns the ObjectId id as a 24 character hex string representation
static getInc(): number
Update the ObjectId index

@private
static generate(time?: number): Buffer
Generate a 12 byte id buffer used in ObjectId's

- `@param` `time` - pass in a second based timestamp.

toString(format?: string): string
Converts the id into a 24 character hex string for printing

- `@param` `format` - The Buffer toString format parameter.

toJSON(): string
Converts to its JSON the 24 character hex string representation.
equals(otherId: string | ObjectId | ObjectIdLike): boolean
Compares the equality of this ObjectId with `otherID`.

- `@param` `otherId` - ObjectId instance to compare against.

getTimestamp(): Date
Returns the generation date (accurate up to the second) that this ID was generated.
static createPk(): ObjectId

static createFromTime(time: number): ObjectId
Creates an ObjectId from a second based number, with the rest of the ObjectId zeroed out. Used for comparisons or sorting the ObjectId.

- `@param` `time` - an integer number representing a number of seconds.

static createFromHexString(hexString: string): ObjectId
Creates an ObjectId from a hex string representation of an ObjectId.

- `@param` `hexString` - create a ObjectId from a passed in 24 character hexstring.

static isValid(id: string | number | ObjectId | ObjectIdLike | Buffer | Uint8Array): boolean
Checks if a value is a valid bson ObjectId

- `@param` `id` - ObjectId instance to validate.

toExtendedJSON(): ObjectIdExtended

static fromExtendedJSON(doc: ObjectIdExtended): ObjectId

[Symbol.for('nodejs.util.inspect.custom')](): string
Converts to a string representation of this Id.

- `@return` return the 24 character hex string representation.

inspect(): string

### class Timestamp extends LongWithoutOverridesClass


constructor(long: Long)

- `@param` `low` - A 64-bit Long representing the Timestamp.

constructor(value: { t: number; i: number; })

- `@param` `value` - A pair of two values indicating timestamp and increment.

constructor(low: number, high: number)

- `@param` `low` - the low (signed) 32 bits of the Timestamp.

- `@param` `high` - the high (signed) 32 bits of the Timestamp.

@deprecated
 Please use `Timestamp({ t: high, i: low })` or `Timestamp(Long(low, high))` instead.

constructor(low: number | Long | { t: number; i: number; }, high?: number)
- `_bsontype: "Timestamp"` 
- `static readonly MAX_VALUE` 
toJSON(): { $timestamp: string; }
static fromInt(value: number): Timestamp
Returns a Timestamp represented by the given (32-bit) integer value.
static fromNumber(value: number): Timestamp
Returns a Timestamp representing the given number value, provided that it is a finite number. Otherwise, zero is returned.
static fromBits(lowBits: number, highBits: number): Timestamp
Returns a Timestamp for the given high and low bits. Each is assumed to use 32 bits.

- `@param` `lowBits` - the low 32-bits.

- `@param` `highBits` - the high 32-bits.

static fromString(str: string, optRadix: number): Timestamp
Returns a Timestamp from the given string, optionally using the given radix.

- `@param` `str` - the textual representation of the Timestamp.

- `@param` `optRadix` - the radix in which the text is written.

toExtendedJSON(): TimestampExtended

static fromExtendedJSON(doc: TimestampExtended): Timestamp

[Symbol.for('nodejs.util.inspect.custom')](): string

inspect(): string

### class UUID
A class representation of the BSON UUID type.


constructor(input?: string | Buffer | UUID)
Create an UUID type

- `@param` `input` - Can be a 32 or 36 character hex string (dashes excluded/included) or a 16 byte binary Buffer.

- `_bsontype: "UUID"` 
- `static cacheHexString: boolean` 
- `private [kId]: Buffer` 
UUID Bytes @internal
- `private __id?: string` 
UUID hexString cache @internal
get id(): Buffer
The UUID bytes

@readonly
set id(value: Buffer)
toHexString(includeDashes): string
Returns the UUID id as a 32 or 36 character hex string representation, excluding/including dashes (defaults to 36 character dash separated)

- `@param` `includeDashes` - should the string exclude dash-separators.

toString(encoding?: string): string
Converts the id into a 36 character (dashes included) hex string, unless a encoding is specified.
toJSON(): string
Converts the id into its JSON string representation.
A 36 character (dashes included) hex string in the format: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
equals(otherId: string | Buffer | UUID): boolean
Compares the equality of this UUID with `otherID`.

- `@param` `otherId` - UUID instance to compare against.

toBinary(): Binary
Creates a Binary instance from the current UUID.
static generate(): Buffer
Generates a populated buffer containing a v4 uuid
static isValid(input: string | Buffer | UUID): boolean
Checks if a value is a valid bson UUID

- `@param` `input` - UUID, string or Buffer to validate.

static createFromHexString(hexString: string): UUID
Creates an UUID from a hex string representation of an UUID.

- `@param` `hexString` - 32 or 36 character hex string (dashes excluded/included).

[Symbol.for('nodejs.util.inspect.custom')](): string
Converts to a string representation of this Id.

- `@return` return the 36 character hex string representation.

inspect(): string

### `interface` `BSONRegExpExtended`


$regularExpression: { pattern: string; options: string; }

### `interface` `BSONRegExpExtendedLegacy`


$regex: string | BSONRegExp
$options: string

### `interface` `BSONSymbolExtended`


$symbol: string

### `interface` `BinaryExtended`


$binary: { subType: string; base64: string; }

### `interface` `BinaryExtendedLegacy`


$type: string
$binary: string

### `interface` `CodeExtended`


$code: string | Function
$scope?: Document

### `interface` `DBRefLike`


$ref: string
$id: ObjectId
$db?: string

### `interface` `Decimal128Extended`


$numberDecimal: string

### `interface` `DeserializeOptions`


evalFunctions?: boolean
evaluate functions in the BSON document scoped to the object deserialized.
cacheFunctions?: boolean
cache evaluated functions for reuse.
cacheFunctionsCrc32?: boolean
use a crc32 code for caching, otherwise use the string of the function.

@deprecated
 this option to use the crc32 function never worked as intended
 due to the fact that the crc32 function itself was never implemented.

promoteLongs?: boolean
when deserializing a Long will fit it into a Number if it's smaller than 53 bits
promoteBuffers?: boolean
when deserializing a Binary will return it as a node.js Buffer instance.
promoteValues?: boolean
when deserializing will promote BSON values to their Node.js closest equivalent types.
fieldsAsRaw?: Document
allow to specify if there what fields we wish to return as unserialized raw buffer.
bsonRegExp?: boolean
return BSON regular expressions as BSONRegExp instances.
allowObjectSmallerThanBufferSize?: boolean
allows the buffer to be larger than the parsed BSON object
index?: number
Offset into buffer to begin reading document from
raw?: boolean
validation?: { utf8: boolean | Record<string, true> | Record<string, false>; }
Allows for opt-out utf-8 validation for all keys or
specified keys. Must be all true or all false.

@example
 ```js
 // disables validation on all keys
  validation: { utf8: false }
 
 // enables validation only on specified keys a, b, and c
  validation: { utf8: { a: true, b: true, c: true } }
 
  // disables validation only on specified keys a, b
  validation: { utf8: { a: false, b: false } }
 ```


### `interface` `Document`


[key: string]: any

### `interface` `DoubleExtended`


$numberDouble: string

### `interface` `Int32Extended`


$numberInt: string

### `interface` `LongExtended`


$numberLong: string

### `interface` `MaxKeyExtended`


$maxKey: 1

### `interface` `MinKeyExtended`


$minKey: 1

### `interface` `ObjectIdExtended`


$oid: string

### `interface` `ObjectIdLike`


id: string | Buffer
__id?: string
toHexString(): string

### `interface` `SerializeOptions`


checkKeys?: boolean
the serializer will check if keys are valid.
serializeFunctions?: boolean
serialize the javascript functions **(default:false)**.
ignoreUndefined?: boolean
serialize will not emit undefined fields **(default:true)**
minInternalBufferSize?: number

@@internal Resize internal buffer
index?: number
the index in the buffer where we wish to start serializing into

### `interface` `TimestampExtended`


$timestamp: { t: number; i: number; }

### type BinarySequence = Uint8Array | Buffer | number[]


### type CalculateObjectSizeOptions = Pick<SerializeOptions, "serializeFunctions" | "ignoreUndefined">


### type EJSONOptions = EJSON.Options


### type LongWithoutOverrides = new (low: unknown, high?: number, unsigned?: boolean) => [P in Exclude<keyof Long, TimestampOverrides>]: Long[P]


### type TimestampOverrides = "_bsontype" | "toExtendedJSON" | "fromExtendedJSON" | "inspect"


### type UUIDExtended = { $uuid: string; }


### namespace EJSON
EJSON parse / stringify API


### `interface` `Options`
### `function parse(text: string, options?: EJSON.Options): SerializableTypes`
Parse an Extended JSON string, constructing the JavaScript value or object described by that
string.

@example
 ```js
 const { EJSON } = require('bson');
 const text = '{ "int32": { "$numberInt": "10" } }';
 
 // prints { int32: { [String: '10'] _bsontype: 'Int32', value: '10' } }
 console.log(EJSON.parse(text, { relaxed: false }));
 
 // prints { int32: 10 }
 console.log(EJSON.parse(text));
 ```

### type JSONPrimitive = string | number | boolean | null
### type SerializableTypes = Document | Array<JSONPrimitive | Document> | JSONPrimitive
### `function stringify(value: SerializableTypes, replacer?: (number | string)[] | ((this: any, key: string, value: any) => any) | EJSON.Options, space?: string | number, options?: EJSON.Options): string`
Converts a BSON document to an Extended JSON string, optionally replacing values if a replacer
function is specified or optionally including only the specified properties if a replacer array
is specified.

- `@param` `value` - The value to convert to extended JSON

- `@param` `replacer` - A function that alters the behavior of the stringification process, or an array of String and Number objects that serve as a whitelist for selecting/filtering the properties of the value object to be included in the JSON string. If this value is null or not provided, all properties of the object are included in the resulting JSON string

- `@param` `space` - A String or Number object that's used to insert white space into the output JSON string for readability purposes.

- `@param` `options` - Optional settings

@example
 ```js
 const { EJSON } = require('bson');
 const Int32 = require('mongodb').Int32;
 const doc = { int32: new Int32(10) };
 
 // prints '{"int32":{"$numberInt":"10"}}'
 console.log(EJSON.stringify(doc, { relaxed: false }));
 
 // prints '{"int32":10}'
 console.log(EJSON.stringify(doc));
 ```

### `function serialize(value: SerializableTypes, options?: EJSON.Options): Document`
Serializes an object to an Extended JSON string, and reparse it as a JavaScript object.

- `@param` `value` - The object to serialize

- `@param` `options` - Optional settings passed to the `stringify` function

### `function deserialize(ejson: Document, options?: EJSON.Options): SerializableTypes`
Deserializes an Extended JSON object into a plain JavaScript object with native/BSON types

- `@param` `ejson` - The Extended JSON object to deserialize

- `@param` `options` - Optional settings passed to the parse method




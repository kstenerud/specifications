The Specifications Project
==========================

Specifications for better computing.

### Released Specifications:

 * [Compact Float Format](#compact-float-format): An encoding scheme to store floating point values in as few bytes as possible.
 * [Compact Time Format](#compact-time-format): An encoding scheme to store dates, times, and timestamps, down to the nanosecond, in as few bytes as possible.
 * [Safe Text Encoding](#safe-text-encoding): Binary to text encoding for modern systems.
 * [Smalltime](#smalltime): Binary date & time format in 64 bits.
 * [Variable Bit Padding](#variable-bit-padding): Arbitrary length variable bit-level padding.
 * [Variable Length Quantity](#variable-length-quantity): An encoding scheme to compress unsigned integers.
 * [Varpad](#varpad): Unlimited padding with an embedded length field.

### Late Development (unlikely to change much):

 * [Concise Binary and Text Encoding](#concise-binary-and-text-encoding): General purpose, compact representations of semi-structured hierarchical data, in binary and text formats.

### Early Development (likely to change):

 * [Streamux](#streamux): A minimalist, asynchronous, multiplexing, request-response protocol.

---------------------------------------------------------------------


Compact Float Format
--------------------

Compact float format is an encoding scheme to store a decimal floating point value in as few bytes as possible for data transmission.

Compact float can store all of the kinds of values that the ieee754 decimal types can, without data loss:

* ±0
* ±infinity
* Signaling and quiet NaNs, including payload

#### Specification

* [Compact Float Specification](https://github.com/kstenerud/compact-float/blob/master/compact-float-specification.md)

#### Implementation

* TODO

#### Status: Prerelease

#### Alternative To:

* IEEE754 Floating point

---------------------------------------------------------------------


Compact Time Format
-------------------

An encoding scheme to store dates, times, and timestamps, down to the nanosecond, in as few bytes as possible.

#### Features

 * Encodes a date into as few as 3 bytes.
 * Encodes a time into as few as 4 bytes.
 * Encodes a timestamp into as few as 5 bytes.
 * Supports unlimited positive and negative year values.
 * Supports time units down to the nanosecond.
 * Supports leap years and leap seconds.
 * Maintenance-free (no leap second tables to update).
 * Efficient conversion to/from human readable fields (no multiplication or division).
 * Time zones are location-based.

#### Specification

* [Compact Time Specification](https://github.com/kstenerud/compact-time/blob/master/compact-time-specification.md)

#### Implementation

* [C Implementation](https://github.com/kstenerud/compact-time/blob/master/reference-implementation)

#### Status: Prerelease

#### Alternative To:

* [Smalltime](#smalltime)

---------------------------------------------------------------------


Concise Binary and Text Encoding
--------------------------------

CBE and CTE are general purpose, compact representations of semi-structured hierarchical data, in binary and text formats. They support all common data types, including dates, URIs, and decimal floating point values.

CBE is designed to encode more commonly used types and values in a shorter space.

#### Features

  * General purpose encoding for a large number of applications
  * Supports the most common data types
  * Supports hierarchical data structuring
  * Minimal complexity
  * Type compatibility between CBE and CTE

#### Features: Concise Binary Encoding (CBE)

  * Binary format to minimize parsing costs
  * Little endian byte ordering to allow the most common systems to read directly off the wire
  * Balanced space and computation efficiency

#### Features: Concise Text Encoding (CTE)

  * Human readable format

#### Specifications

* [CBE Specification](https://github.com/kstenerud/concise-binary-encoding/blob/master/cbe-specification.md)
* [CTE Specification](https://github.com/kstenerud/concise-text-encoding/blob/master/cte-specification.md)

#### Implementations

* [C Implementation](https://github.com/kstenerud/concise-binary-encoding/tree/master/reference-implementation)
* [Go Implementation](https://github.com/kstenerud/go-cbe)

#### Status: Prerelease

#### Alternative To:

* JSON
* XML
* BSON
* CBOR
* MessagePack
* Protobuf

---------------------------------------------------------------------


Safe Text Encoding
------------------

Binary data encoding schemes that are safe to be passed through modern processing systems that expect human readable text, without requiring escaping.

#### Features: All

 * Safe for use in JSON, SGML formats, source code strings, without escaping
 * Safe for use in path, query, and fragment components of URIs
 * Safe for use in formatted documents
 * Safe for use in legacy text processing systems
 * Support for length fields
 * Liberal whitespace rules
 * No padding characters
 * Safe for use in filenames on POSIX file systems
 * Sortable in generic text sorting algorithms (such as file listings)

#### Features: Safe80 and below

 * Safe for use in filenames on Windows file systems

#### Features: Safe64 and below

 * Safe for use in all URI components without escaping

#### Features: Safe32 and below

 * Useful for human input situations such as activation codes
 * Easily confusable characters & digits are interchangeable
 * Uppercase and lowercase characters are interchangeable

#### Specification

* [Safe16 Specification](https://github.com/kstenerud/safe-encoding/blob/master/safe16-specification.md)
* [Safe32 Specification](https://github.com/kstenerud/safe-encoding/blob/master/safe32-specification.md)
* [Safe64 Specification](https://github.com/kstenerud/safe-encoding/blob/master/safe64-specification.md)
* [Safe80 Specification](https://github.com/kstenerud/safe-encoding/blob/master/safe80-specification.md)
* [Safe85 Specification](https://github.com/kstenerud/safe-encoding/blob/master/safe85-specification.md)

#### Implementation

* [C Implementation](https://github.com/kstenerud/safe-encoding/blob/master/reference-implementation)

#### Status: Released

#### Alternative To:

* Base16
* Base32
* Base64
* Ascii85

---------------------------------------------------------------------


Smalltime
---------

Smalltime offers a simple and convenient way to encode date & time values into signed 64-bit integers that are comparable.

#### Features

 * Encodes a complete date & time into a 64-bit signed integer.
 * Fields (including year) are compatible with ISO-8601.
 * Maintenance-free (no leap second tables to update).
 * Easily converts to human readable fields.
 * Supports hundreds of thousands of years.
 * Supports time units to the microsecond.
 * Supports leap years and leap seconds.
 * Values are in timezone zero by default.
 * Encoded values are comparable.

#### Specification

* [Smalltime Specification](https://github.com/kstenerud/smalltime/blob/master/smalltime-specification.md)
* [Nanotime Specification](https://github.com/kstenerud/smalltime/blob/master/nanotime-specification.md)

#### Implementation

* [C Implementation](https://github.com/kstenerud/smalltime/blob/master/reference-implementation)
* [Go Implementation](https://github.com/kstenerud/go-smalltime)

#### Status: Released

#### Alternative To:

* [Compact Time Format](#compact-time-format)

---------------------------------------------------------------------


Streamux
--------

A minimalist, asynchronous, multiplexing, request-response protocol.

A minimalist, asynchronous, multiplexing, request-response protocol.

Streamux is designed as a low level, point-to-point, bidirectional protocol for you to build a messaging layer on top of. It handles the nitty gritty things like initialization, multiplexing, asynchronous operation, and packetization of your messages.

The only additional components required are:

* A reliable communication transport (TCP, pipes, RS-232, etc)
* A message encoding format & marshaling scheme (for example [CBE](https://github.com/kstenerud/concise-encoding/blob/master/cbe-specification.md))
* Endpoints to receive the messages.

#### Features

* Minimal Overhead (1 to 4 bytes per message chunk, depending on configuration)
* Multiplexing (multiple data streams can be sent across a single channel)
* Asynchronous (client is informed asynchronously upon completion or error)
* Interruptible (requests may be canceled)
* Floating roles (both peers can operate as client and server at the same time)
* Quick init mode for faster initialization

#### Specification

* [Streamux Specification](https://github.com/kstenerud/streamux/blob/master/streamux-specification.md)

#### Implementation

* [Go Implementation](https://github.com/kstenerud/go-streamux)

#### Status: Prerelease

---------------------------------------------------------------------


Variable Bit Padding
--------------------

A scheme for encoding an arbitrary number of padding bits in a field or bit stream.

#### Features

* Padding can be decoded from the left or right side.
* Padding can be 0-based (filled with `0` bits) or 1-based (filled with `1` bits).

#### Specification

* [Variable Bit Padding Specification](https://github.com/kstenerud/variable-bit-padding/blob/master/variable-bit-padding-specification.md)

#### Implementation

* TODO

#### Status: Released

---------------------------------------------------------------------


Variable Length Quantity
------------------------

Variable Length Quantity (VLQ) encoding is an unsigned integer compression scheme originally designed for the MIDI file format. This specification expands upon it slightly by allowing encoding from the "left" or "right" side of the quantity (the original MIDI version is "right" oriented).

#### Features

 * Left or right oriented encoding
 * Supports progressive decoding

#### Specification

* [VLQ Specification](https://github.com/kstenerud/vlq/blob/master/vlq-specification.md)

#### Implementation

* [Go Implementation](https://github.com/kstenerud/go-vlq)

#### Status: Released

#### Alternative To:

* [Protobuf Varint](https://developers.google.com/protocol-buffers/docs/encoding#varints)

---------------------------------------------------------------------


Varpad
------

Varpad is a padding encoding scheme that allows unambiguous detection of the padding length without requiring an external field. It is similar to the scheme described in [PKCS#7](http://tools.ietf.org/html/rfc5652#section-6.3), but doesn't suffer from its limitations (PKCS#7 padding has a length limit of 255).

#### Features

 * Doesn't require a separate length field (the length is embedded in the padding itself).
 * Padding length can be unambiguously detected by examining the first or last byte.
 * No upper limit on padding length.

#### Specification

* [Varpad Specification](https://github.com/kstenerud/varpad/blob/master/varpad-specification.md)

#### Implementation

* [Go Implementation](https://github.com/kstenerud/go-varpad)

#### Status: Released

#### Alternative To:

* [PKCS#7](http://tools.ietf.org/html/rfc5652#section-6.3)

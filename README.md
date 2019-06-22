The Specifications Project
==========================

Specifications for better computing.


 * [Smalltime](#smalltime): Binary date & time format in 64 bits.
 * [Varpad](#varpad): Unlimited padding with an embedded length field.
 * [Variable Length Quantity](#variable-length-quantity): An encoding scheme to compress unsigned integers.
 * [Safe Text Encoding](#safe-text-encoding): Binary to text encoding for modern systems.
 * [Concise Binary and Text Encoding](#concise-binary-and-text-encoding): General purpose, compact representations of semi-structured hierarchical data, in binary and text formats.
 * [Streamux](#streamux): A minimalist, asynchronous, multiplexing, request-response protocol.

---------------------------------------------------------------------


Smalltime
---------

Binary date & time format in 64 bits.

[Smalltime Specification](https://github.com/kstenerud/smalltime/blob/master/smalltime-specification.md)

#### Status: Released

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

---------------------------------------------------------------------


Varpad
------

Unlimited padding with an embedded length field.

[Varpad Specification](https://github.com/kstenerud/varpad/blob/master/varpad-specification.md)

#### Status: Released

Varpad is a padding encoding scheme that allows unambiguous detection of the padding length without requiring an external field. It is similar to the scheme described in [PKCS#7](http://tools.ietf.org/html/rfc5652#section-6.3), but doesn't suffer from its limitations (PKCS#7 padding has a length limit of 255).


#### Alternative To:

* [PKCS#7](http://tools.ietf.org/html/rfc5652#section-6.3)


#### Features

 * Doesn't require a separate length field (the length is embedded in the padding itself).
 * Padding length can be unambiguously detected by examining the first or last byte of the payload (depending on the ordering of message and padding).
 * No upper limit on padding length.


---------------------------------------------------------------------


Variable Length Quantity
------------------------

An encoding scheme to compress unsigned integers.

[VLQ Specification](https://github.com/kstenerud/vlq/blob/master/vlq-specification.md)

#### Status: Released

Variable Length Quantity (VLQ) encoding is an unsigned integer compression scheme designed for the MIDI file format.


#### Alternative To:

* [Protobuf Varint](https://developers.google.com/protocol-buffers/docs/encoding#varints)


#### Features

 * Forward or reverse encoding
 * Supports progressive decoding

---------------------------------------------------------------------


Safe Text Encoding
------------------

Binary to text encoding for modern systems.

[Safe16 Specification](https://github.com/kstenerud/safe-encoding/blob/master/safe16-specification.md)

[Safe32 Specification](https://github.com/kstenerud/safe-encoding/blob/master/safe32-specification.md)

[Safe64 Specification](https://github.com/kstenerud/safe-encoding/blob/master/safe64-specification.md)

[Safe80 Specification](https://github.com/kstenerud/safe-encoding/blob/master/safe80-specification.md)

[Safe85 Specification](https://github.com/kstenerud/safe-encoding/blob/master/safe85-specification.md)

#### Status: Released

Binary data encoding schemes that are safe to be passed through processing systems that expect human readable text, without requiring escaping.

#### Alternative To:

* Base16
* Base32
* Base64
* Ascii85


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

---------------------------------------------------------------------


Concise Binary and Text Encoding
--------------------------------

General purpose, compact representations of semi-structured hierarchical data, in binary and text formats.

[CBE Specification](https://github.com/kstenerud/concise-encoding/blob/master/cbe-specification.md)

[CTE Specification](https://github.com/kstenerud/concise-encoding/blob/master/cte-specification.md)

#### Status: Prerelease

CBE and CTE are general purpose, compact representations of semi-structured hierarchical data, in binary and text formats. They support all common data types, including dates, URIs, and decimal floating point values.

CBE is designed to encode more commonly used types and values in a shorter space.


#### Alternative To:

* JSON
* XML
* BSON
* CBOR
* MessagePack
* Protobuf


#### Features

  * General purpose encoding for a large number of applications
  * Supports the most common data types
  * Supports hierarchical data structuring
  * Minimal complexity
  * Type compatibility between [CBE](https://github.com/kstenerud/concise-binary-encoding/blob/master/cbe-specification.md) and [CTE](https://github.com/kstenerud/concise-binary-encoding/blob/master/cte-specification.md)

#### Features: Concise Binary Encoding (CBE)

  * Binary format to minimize parsing costs
  * Little endian byte ordering to allow the most common systems to read directly off the wire
  * Balanced space and computation efficiency

#### Features: Concise Text Encoding (CTE)

  * Human readable format

---------------------------------------------------------------------


Streamux
--------

A minimalist, asynchronous, multiplexing, request-response protocol.

[Streamux Specification](https://github.com/kstenerud/streamux/blob/master/streamux-specification.md)

#### Status: Prerelease

A minimalist, asynchronous, multiplexing, request-response protocol.

Streamux is designed as a low level, point-to-point, bidirectional protocol for you to build a messaging layer on top of. It handles the nitty gritty things like initialization, multiplexing, asynchronous operation, and packetization of your messages.

The only additional components required are:

* A reliable communication transport (TCP, pipes, RS-232, etc)
* A message encoding format & marshaling scheme (for example [CBE](https://github.com/kstenerud/concise-encoding/blob/master/cbe-specification.md))
* Endpoints to receive the messages.


### Features

* Minimal Overhead (1 to 4 bytes per message chunk, depending on configuration)
* Multiplexing (multiple data streams can be sent across a single channel)
* Asynchronous (client is informed asynchronously upon completion or error)
* Interruptible (requests may be canceled)
* Floating roles (both peers can operate as client and server at the same time)
* Quick init mode for faster initialization

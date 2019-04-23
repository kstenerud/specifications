Specifications
==============

A pointer to the specifications I've published.


Specifications
--------------

 * [Smalltime](#smalltime)
 * [Safe Text Encoding](#safe-text-encoding)
 * [Concise Binary and Text Encoding](#concise-binary-and-text-encoding)
 * [Streamux](#streamux)

---------------------------------------------------------------------


Smalltime
---------

[https://github.com/kstenerud/smalltime](https://github.com/kstenerud/smalltime)

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
 * Values are always in timezone zero.
 * Encoded values are comparable.

---------------------------------------------------------------------


Safe Text Encoding
------------------

[https://github.com/kstenerud/safe-encoding](https://github.com/kstenerud/safe-encoding)

#### Status: Released

Binary data encoding schemes that are safe to be passed through processing systems that expect human readable text, without requiring escaping.


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

[https://github.com/kstenerud/concise-binary-encoding](https://github.com/kstenerud/concise-binary-encoding)

#### Status: Prerelease

General purpose, compact representations of semi-structured hierarchical data, in binary and text formats.


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

[https://github.com/kstenerud/streamux](https://github.com/kstenerud/streamux)

#### Status: Prerelease

A minimalist, asynchronous, multiplexing, request-response protocol.


#### Features

* Minimal Overhead (1 to 4 bytes per message chunk, depending on configuration)
* Multiplexing (multiple data streams can be sent across a single channel)
* Asynchronous (client is informed asynchronously upon completion or error)
* Interruptible (requests may be canceled)
* Floating roles (both peers can operate as client and server at the same time)

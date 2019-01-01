Specifications
==============

A pointer to the specifications I've published.


Specifications
--------------

 * [Smalltime](#smalltime)
 * [Safe64 and Safe32](#safe64-and-safe32)
 * [Concise Binary and Text Encoding](#concise-binary-and-text-encoding)

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


Safe64 and Safe32
-----------------

[https://github.com/kstenerud/safe64](https://github.com/kstenerud/safe64)

#### Status: Prerelease

[Safe64](https://github.com/kstenerud/safe64/blob/master/safe64-specification.md) and [safe32](https://github.com/kstenerud/safe64/blob/master/safe32-specification.md) define binary data encoding schemes that are safe to be passed through processing systems that expect human readable text.

#### Features

 * No escaping necessary
 * Safe for use in URLs
 * Safe for use as filenames
 * Safe for use in formatted documents
 * Safe for use in legacy text processing systems
 * Liberal whitespace rules
 * Sortable in generic text sorting algorithms (such as file listings)
 * Alternate form with prefixed length

#### Safe32 Additional Features:

 * Easily confusable characters & digits are interchangeable.
 * Uppercase and lowercase characters are interchangeable.

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

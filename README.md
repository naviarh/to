forked from **[spf13/cast](https://github.com/spf13/cast)**

To
==

Easy and safe casting from one type to another in Go

## What is this?

"**To**" is a library to convert between different go types in a consistent and easy way.

"**To**" provides simple functions to easily convert a number to a string, an
interface into a bool, etc. "**To**" does this intelligently when an obvious
conversion is possible. It doesn’t make any attempts to guess what you meant,
for example you can only convert a string to an int when it is a string
representation of an int such as “8”.

## Why use this?

When working with dynamic data in Go you often need to "To" or convert the data
from one type into another. "**To**" goes beyond just using type assertion (though
it uses that when possible) to provide a very straightforward and convenient
library.

If you are working with interfaces to handle things like dynamic content
you’ll need an easy way to convert an interface into a given type. This
is the library for you.

If you are taking in data from YAML, TOML or JSON or other formats which lack
full types, then "**To**" is the library for you.

## Usage

"**To**" provides a handful of to._____ methods. These methods will always return
the desired type. **If input is provided that will not convert to that type, the
0 or nil value for that type will be returned**.

"**To**" also provides identical methods to._____E. These return the same result as
the to._____ methods, plus an additional error which tells you if it successfully
converted. Using these methods you can tell the difference between when the
input matched the zero value or when the conversion failed and the zero value
was returned.

The following examples are merely a sample of what is available. Please review
the code for a complete set.

### Example ‘String’:

    to.String("mayonegg")         // "mayonegg"
    to.String(8)                  // "8"
    to.String(8.31)               // "8.31"
    to.String([]byte("one time")) // "one time"
    to.String(nil)                // ""

	var foo interface{} = "one more time"
    to.String(foo)                // "one more time"


### Example ‘Int’:

    to.Int(8)                  // 8
    to.Int(8.31)               // 8
    to.Int("8")                // 8
    to.Int(true)               // 1
    to.Int(false)              // 0

	var eight interface{} = 8
    to.Int(eight)              // 8
    to.Int(nil)                // 0


### 2 ways to use the library

	**import "https://github.com/naviarh/to"**

This method involves writing an additional word to function names, for example:

	to.Int(..), to.Float64(..), to.String(..)

	**import . "https://github.com/naviarh/to"**

This method removes the need for a prefix, but you must ensure that there are no conflicts with other libraries. Examples:

	Int(..), Float64(..), String(..)



## UMRN

--------


### Installation

```
npm install umrn
```


### Basic Usage

```
const UMRN = require('umrn');

var myUmrn = new UMRN({...options});
myUmrn.validate(); //true
```


### A breakdown of the UMRN format

#### Background

Each UMRN is intended to be universally unique, with the
probability of a collision limited only by the underlying
[PRNG](https://en.wikipedia.org/wiki/Pseudorandom_number_generator)
engine available on the generating system. Similar to UUIDs, UMRNs
follow strict formatting conventions and encode structured
metadata within the content of the identifier itself. Unlike
UUIDs however, UMRNs have no notion of versioning.
The UMRN specification was not designed to be extensible, and thus
all UMRNs are expected to adhere to the exact standard with no
ability for an UMRN to include metadata that explicitly declares
support for additional features or capabilities beyond what is
defined in the specification.


#### Structure

UMRNs were designed to be compact, human-readable and easily
memorized.


Taking the following UMRN as an example:
```
65163687965107819837260518650328226017350261448293
```

We can extract the following components:

```
651 6 36879651078198372605186503282260173 50261448293
--- - ----------------------------------- -----------
|   | |                                   |
|   | |                     HMAC Signature|
|   | |Body Content
|   |
|   |Checksum Byte
|
|Preamble


```


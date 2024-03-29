Package bytes
=============

-   `import "bytes"`
-   [Overview](#pkg-overview)
-   [Index](#pkg-index)
-   [Examples](#pkg-examples)

Overview 
--------

Package bytes implements functions for the manipulation of byte slices.
It is analogous to the facilities of the strings package.

Index 
-----

-   [Constants](#pkg-constants)
-   [Variables](#pkg-variables)
-   [func Clone(b \[\]byte) \[\]byte](#Clone)
-   [func Compare(a, b \[\]byte) int](#Compare)
-   [func Contains(b, subslice \[\]byte) bool](#Contains)
-   [func ContainsAny(b \[\]byte, chars string) bool](#ContainsAny)
-   [func ContainsFunc(b \[\]byte, f func(rune) bool)
    bool](#ContainsFunc)
-   [func ContainsRune(b \[\]byte, r rune) bool](#ContainsRune)
-   [func Count(s, sep \[\]byte) int](#Count)
-   [func Cut(s, sep \[\]byte) (before, after \[\]byte, found
    bool)](#Cut)
-   [func CutPrefix(s, prefix \[\]byte) (after \[\]byte, found
    bool)](#CutPrefix)
-   [func CutSuffix(s, suffix \[\]byte) (before \[\]byte, found
    bool)](#CutSuffix)
-   [func Equal(a, b \[\]byte) bool](#Equal)
-   [func EqualFold(s, t \[\]byte) bool](#EqualFold)
-   [func Fields(s \[\]byte) \[\]\[\]byte](#Fields)
-   [func FieldsFunc(s \[\]byte, f func(rune) bool)
    \[\]\[\]byte](#FieldsFunc)
-   [func HasPrefix(s, prefix \[\]byte) bool](#HasPrefix)
-   [func HasSuffix(s, suffix \[\]byte) bool](#HasSuffix)
-   [func Index(s, sep \[\]byte) int](#Index)
-   [func IndexAny(s \[\]byte, chars string) int](#IndexAny)
-   [func IndexByte(b \[\]byte, c byte) int](#IndexByte)
-   [func IndexFunc(s \[\]byte, f func(r rune) bool) int](#IndexFunc)
-   [func IndexRune(s \[\]byte, r rune) int](#IndexRune)
-   [func Join(s \[\]\[\]byte, sep \[\]byte) \[\]byte](#Join)
-   [func LastIndex(s, sep \[\]byte) int](#LastIndex)
-   [func LastIndexAny(s \[\]byte, chars string) int](#LastIndexAny)
-   [func LastIndexByte(s \[\]byte, c byte) int](#LastIndexByte)
-   [func LastIndexFunc(s \[\]byte, f func(r rune) bool)
    int](#LastIndexFunc)
-   [func Map(mapping func(r rune) rune, s \[\]byte) \[\]byte](#Map)
-   [func Repeat(b \[\]byte, count int) \[\]byte](#Repeat)
-   [func Replace(s, old, new \[\]byte, n int) \[\]byte](#Replace)
-   [func ReplaceAll(s, old, new \[\]byte) \[\]byte](#ReplaceAll)
-   [func Runes(s \[\]byte) \[\]rune](#Runes)
-   [func Split(s, sep \[\]byte) \[\]\[\]byte](#Split)
-   [func SplitAfter(s, sep \[\]byte) \[\]\[\]byte](#SplitAfter)
-   [func SplitAfterN(s, sep \[\]byte, n int)
    \[\]\[\]byte](#SplitAfterN)
-   [func SplitN(s, sep \[\]byte, n int) \[\]\[\]byte](#SplitN)
-   [func Title(s \[\]byte) \[\]byte](#Title)
-   [func ToLower(s \[\]byte) \[\]byte](#ToLower)
-   [func ToLowerSpecial(c unicode.SpecialCase, s \[\]byte)
    \[\]byte](#ToLowerSpecial)
-   [func ToTitle(s \[\]byte) \[\]byte](#ToTitle)
-   [func ToTitleSpecial(c unicode.SpecialCase, s \[\]byte)
    \[\]byte](#ToTitleSpecial)
-   [func ToUpper(s \[\]byte) \[\]byte](#ToUpper)
-   [func ToUpperSpecial(c unicode.SpecialCase, s \[\]byte)
    \[\]byte](#ToUpperSpecial)
-   [func ToValidUTF8(s, replacement \[\]byte) \[\]byte](#ToValidUTF8)
-   [func Trim(s \[\]byte, cutset string) \[\]byte](#Trim)
-   [func TrimFunc(s \[\]byte, f func(r rune) bool) \[\]byte](#TrimFunc)
-   [func TrimLeft(s \[\]byte, cutset string) \[\]byte](#TrimLeft)
-   [func TrimLeftFunc(s \[\]byte, f func(r rune) bool)
    \[\]byte](#TrimLeftFunc)
-   [func TrimPrefix(s, prefix \[\]byte) \[\]byte](#TrimPrefix)
-   [func TrimRight(s \[\]byte, cutset string) \[\]byte](#TrimRight)
-   [func TrimRightFunc(s \[\]byte, f func(r rune) bool)
    \[\]byte](#TrimRightFunc)
-   [func TrimSpace(s \[\]byte) \[\]byte](#TrimSpace)
-   [func TrimSuffix(s, suffix \[\]byte) \[\]byte](#TrimSuffix)
-   [type Buffer](#Buffer)
-   [func NewBuffer(buf \[\]byte) \*Buffer](#NewBuffer)
-   [func NewBufferString(s string) \*Buffer](#NewBufferString)
-   [func (b \*Buffer) Available() int](#Buffer.Available)
-   [func (b \*Buffer) AvailableBuffer()
    \[\]byte](#Buffer.AvailableBuffer)
-   [func (b \*Buffer) Bytes() \[\]byte](#Buffer.Bytes)
-   [func (b \*Buffer) Cap() int](#Buffer.Cap)
-   [func (b \*Buffer) Grow(n int)](#Buffer.Grow)
-   [func (b \*Buffer) Len() int](#Buffer.Len)
-   [func (b \*Buffer) Next(n int) \[\]byte](#Buffer.Next)
-   [func (b \*Buffer) Read(p \[\]byte) (n int, err
    error)](#Buffer.Read)
-   [func (b \*Buffer) ReadByte() (byte, error)](#Buffer.ReadByte)
-   [func (b \*Buffer) ReadBytes(delim byte) (line \[\]byte, err
    error)](#Buffer.ReadBytes)
-   [func (b \*Buffer) ReadFrom(r io.Reader) (n int64, err
    error)](#Buffer.ReadFrom)
-   [func (b \*Buffer) ReadRune() (r rune, size int, err
    error)](#Buffer.ReadRune)
-   [func (b \*Buffer) ReadString(delim byte) (line string, err
    error)](#Buffer.ReadString)
-   [func (b \*Buffer) Reset()](#Buffer.Reset)
-   [func (b \*Buffer) String() string](#Buffer.String)
-   [func (b \*Buffer) Truncate(n int)](#Buffer.Truncate)
-   [func (b \*Buffer) UnreadByte() error](#Buffer.UnreadByte)
-   [func (b \*Buffer) UnreadRune() error](#Buffer.UnreadRune)
-   [func (b \*Buffer) Write(p \[\]byte) (n int, err
    error)](#Buffer.Write)
-   [func (b \*Buffer) WriteByte(c byte) error](#Buffer.WriteByte)
-   [func (b \*Buffer) WriteRune(r rune) (n int, err
    error)](#Buffer.WriteRune)
-   [func (b \*Buffer) WriteString(s string) (n int, err
    error)](#Buffer.WriteString)
-   [func (b \*Buffer) WriteTo(w io.Writer) (n int64, err
    error)](#Buffer.WriteTo)
-   [type Reader](#Reader)
-   [func NewReader(b \[\]byte) \*Reader](#NewReader)
-   [func (r \*Reader) Len() int](#Reader.Len)
-   [func (r \*Reader) Read(b \[\]byte) (n int, err
    error)](#Reader.Read)
-   [func (r \*Reader) ReadAt(b \[\]byte, off int64) (n int, err
    error)](#Reader.ReadAt)
-   [func (r \*Reader) ReadByte() (byte, error)](#Reader.ReadByte)
-   [func (r \*Reader) ReadRune() (ch rune, size int, err
    error)](#Reader.ReadRune)
-   [func (r \*Reader) Reset(b \[\]byte)](#Reader.Reset)
-   [func (r \*Reader) Seek(offset int64, whence int) (int64,
    error)](#Reader.Seek)
-   [func (r \*Reader) Size() int64](#Reader.Size)
-   [func (r \*Reader) UnreadByte() error](#Reader.UnreadByte)
-   [func (r \*Reader) UnreadRune() error](#Reader.UnreadRune)
-   [func (r \*Reader) WriteTo(w io.Writer) (n int64, err
    error)](#Reader.WriteTo)

 
### Examples

[Buffer](#example_Buffer)

[Buffer.AvailableBuffer](#example_Buffer_AvailableBuffer)

[Buffer.Bytes](#example_Buffer_Bytes)

[Buffer.Cap](#example_Buffer_Cap)

[Buffer.Grow](#example_Buffer_Grow)

[Buffer.Len](#example_Buffer_Len)

[Buffer.Next](#example_Buffer_Next)

[Buffer.Read](#example_Buffer_Read)

[Buffer.ReadByte](#example_Buffer_ReadByte)

[Buffer (Reader)](#example_Buffer_reader)

[Clone](#example_Clone)

[Compare](#example_Compare)

[Compare (Search)](#example_Compare_search)

[Contains](#example_Contains)

[ContainsAny](#example_ContainsAny)

[ContainsRune](#example_ContainsRune)

[Count](#example_Count)

[Cut](#example_Cut)

[CutPrefix](#example_CutPrefix)

[CutSuffix](#example_CutSuffix)

[Equal](#example_Equal)

[EqualFold](#example_EqualFold)

[Fields](#example_Fields)

[FieldsFunc](#example_FieldsFunc)

[HasPrefix](#example_HasPrefix)

[HasSuffix](#example_HasSuffix)

[Index](#example_Index)

[IndexAny](#example_IndexAny)

[IndexByte](#example_IndexByte)

[IndexFunc](#example_IndexFunc)

[IndexRune](#example_IndexRune)

[Join](#example_Join)

[LastIndex](#example_LastIndex)

[LastIndexAny](#example_LastIndexAny)

[LastIndexByte](#example_LastIndexByte)

[LastIndexFunc](#example_LastIndexFunc)

[Map](#example_Map)

[Reader.Len](#example_Reader_Len)

[Repeat](#example_Repeat)

[Replace](#example_Replace)

[ReplaceAll](#example_ReplaceAll)

[Runes](#example_Runes)

[Split](#example_Split)

[SplitAfter](#example_SplitAfter)

[SplitAfterN](#example_SplitAfterN)

[SplitN](#example_SplitN)

[Title](#example_Title)

[ToLower](#example_ToLower)

[ToLowerSpecial](#example_ToLowerSpecial)

[ToTitle](#example_ToTitle)

[ToTitleSpecial](#example_ToTitleSpecial)

[ToUpper](#example_ToUpper)

[ToUpperSpecial](#example_ToUpperSpecial)

[ToValidUTF8](#example_ToValidUTF8)

[Trim](#example_Trim)

[TrimFunc](#example_TrimFunc)

[TrimLeft](#example_TrimLeft)

[TrimLeftFunc](#example_TrimLeftFunc)

[TrimPrefix](#example_TrimPrefix)

[TrimRight](#example_TrimRight)

[TrimRightFunc](#example_TrimRightFunc)

[TrimSpace](#example_TrimSpace)

[TrimSuffix](#example_TrimSuffix)


### Package files

buffer.go bytes.go reader.go

Constants 
---------

MinRead is the minimum slice size passed to a Read call by
Buffer.ReadFrom. As long as the Buffer has at least MinRead bytes beyond
what is required to hold the contents of r, ReadFrom will not grow the
underlying buffer.

```go
const MinRead = 512
```

Variables 
---------

ErrTooLarge is passed to panic if memory cannot be allocated to store
data in a buffer.

```go
var ErrTooLarge = errors.New("bytes.Buffer: too large")
```

func Clone 
-------------------------------------------

```go
func Clone(b []byte) []byte
```

Clone returns a copy of b\[:len(b)\]. The result may have additional
unused capacity. Clone(nil) returns nil.

#### [Example]

Code:

```go
b := []byte("abc")
clone := bytes.Clone(b)
fmt.Printf("%s\n", clone)
clone[0] = 'd'
fmt.Printf("%s\n", b)
fmt.Printf("%s\n", clone)
```

Output:

```go
abc
abc
dbc
```

func Compare 
------------

```go
func Compare(a, b []byte) int
```

Compare returns an integer comparing two byte slices lexicographically.
The result will be 0 if a == b, -1 if a \< b, and +1 if a \> b. A nil
argument is equivalent to an empty slice.

#### [Example]

Code:

```go
// Interpret Compare's result by comparing it to zero.
var a, b []byte
if bytes.Compare(a, b) < 0 {
    // a less b
}
if bytes.Compare(a, b) <= 0 {
    // a less or equal b
}
if bytes.Compare(a, b) > 0 {
    // a greater b
}
if bytes.Compare(a, b) >= 0 {
    // a greater or equal b
}

// Prefer Equal to Compare for equality comparisons.
if bytes.Equal(a, b) {
    // a equal b
}
if !bytes.Equal(a, b) {
    // a not equal b
}
```

#### [Example (Search)]

Code:

```go
// Binary search to find a matching byte slice.
var needle []byte
var haystack [][]byte // Assume sorted
i := sort.Search(len(haystack), func(i int) bool {
    // Return haystack[i] >= needle.
    return bytes.Compare(haystack[i], needle) >= 0
})
if i < len(haystack) && bytes.Equal(haystack[i], needle) {
    // Found it!
}
```

func Contains 
-------------

```go
func Contains(b, subslice []byte) bool
```

Contains reports whether subslice is within b.

#### [Example]

Code:

```go
fmt.Println(bytes.Contains([]byte("seafood"), []byte("foo")))
fmt.Println(bytes.Contains([]byte("seafood"), []byte("bar")))
fmt.Println(bytes.Contains([]byte("seafood"), []byte("")))
fmt.Println(bytes.Contains([]byte(""), []byte("")))
```

Output:

```go
true
false
true
true
```

func ContainsAny 
-----------------------------------------------

```go
func ContainsAny(b []byte, chars string) bool
```

ContainsAny reports whether any of the UTF-8-encoded code points in
chars are within b.

#### [Example]

Code:

```go
fmt.Println(bytes.ContainsAny([]byte("I like seafood."), "fÄo!"))
fmt.Println(bytes.ContainsAny([]byte("I like seafood."), "去是伟大的."))
fmt.Println(bytes.ContainsAny([]byte("I like seafood."), ""))
fmt.Println(bytes.ContainsAny([]byte(""), ""))
```

Output:

```go
true
true
false
false
```

func ContainsFunc 
--------------------------------------------------

```go
func ContainsFunc(b []byte, f func(rune) bool) bool
```

ContainsFunc reports whether any of the UTF-8-encoded code points r
within b satisfy f(r).

func ContainsRune 
------------------------------------------------

```go
func ContainsRune(b []byte, r rune) bool
```

ContainsRune reports whether the rune is contained in the UTF-8-encoded
byte slice b.

#### [Example]

Code:

```go
fmt.Println(bytes.ContainsRune([]byte("I like seafood."), 'f'))
fmt.Println(bytes.ContainsRune([]byte("I like seafood."), 'ö'))
fmt.Println(bytes.ContainsRune([]byte("去是伟大的!"), '大'))
fmt.Println(bytes.ContainsRune([]byte("去是伟大的!"), '!'))
fmt.Println(bytes.ContainsRune([]byte(""), '@'))
```

Output:

```go
true
false
true
true
false
```

func Count 
----------

```go
func Count(s, sep []byte) int
```

Count counts the number of non-overlapping instances of sep in s. If sep
is an empty slice, Count returns 1 + the number of UTF-8-encoded code
points in s.

#### [Example]

Code:

```go
fmt.Println(bytes.Count([]byte("cheese"), []byte("e")))
fmt.Println(bytes.Count([]byte("five"), []byte(""))) // before & after each rune
```

Output:

```go
3
5
```

func Cut 
-----------------------------------------

```go
func Cut(s, sep []byte) (before, after []byte, found bool)
```

Cut slices s around the first instance of sep, returning the text before
and after sep. The found result reports whether sep appears in s. If sep
does not appear in s, cut returns s, nil, false.

Cut returns slices of the original slice s, not copies.

#### [Example]

Code:

```go
show := func(s, sep string) {
    before, after, found := bytes.Cut([]byte(s), []byte(sep))
    fmt.Printf("Cut(%q, %q) = %q, %q, %v\n", s, sep, before, after, found)
}
show("Gopher", "Go")
show("Gopher", "ph")
show("Gopher", "er")
show("Gopher", "Badger")
```

Output:

```go
Cut("Gopher", "Go") = "", "pher", true
Cut("Gopher", "ph") = "Go", "er", true
Cut("Gopher", "er") = "Goph", "", true
Cut("Gopher", "Badger") = "Gopher", "", false
```

func CutPrefix 
-----------------------------------------------

```go
func CutPrefix(s, prefix []byte) (after []byte, found bool)
```

CutPrefix returns s without the provided leading prefix byte slice and
reports whether it found the prefix. If s doesn\'t start with prefix,
CutPrefix returns s, false. If prefix is the empty byte slice, CutPrefix
returns s, true.

CutPrefix returns slices of the original slice s, not copies.

#### [Example]

Code:

```go
show := func(s, sep string) {
    after, found := bytes.CutPrefix([]byte(s), []byte(sep))
    fmt.Printf("CutPrefix(%q, %q) = %q, %v\n", s, sep, after, found)
}
show("Gopher", "Go")
show("Gopher", "ph")
```

Output:

```go
CutPrefix("Gopher", "Go") = "pher", true
CutPrefix("Gopher", "ph") = "Gopher", false
```

func CutSuffix 
-----------------------------------------------

```go
func CutSuffix(s, suffix []byte) (before []byte, found bool)
```

CutSuffix returns s without the provided ending suffix byte slice and
reports whether it found the suffix. If s doesn\'t end with suffix,
CutSuffix returns s, false. If suffix is the empty byte slice, CutSuffix
returns s, true.

CutSuffix returns slices of the original slice s, not copies.

#### [Example]

Code:

```go
show := func(s, sep string) {
    before, found := bytes.CutSuffix([]byte(s), []byte(sep))
    fmt.Printf("CutSuffix(%q, %q) = %q, %v\n", s, sep, before, found)
}
show("Gopher", "Go")
show("Gopher", "er")
```

Output:

```go
CutSuffix("Gopher", "Go") = "Gopher", false
CutSuffix("Gopher", "er") = "Goph", true
```

func Equal 
----------

```go
func Equal(a, b []byte) bool
```

Equal reports whether a and b are the same length and contain the same
bytes. A nil argument is equivalent to an empty slice.

#### [Example]

Code:

```go
fmt.Println(bytes.Equal([]byte("Go"), []byte("Go")))
fmt.Println(bytes.Equal([]byte("Go"), []byte("C++")))
```

Output:

```go
true
false
```

func EqualFold 
--------------

```go
func EqualFold(s, t []byte) bool
```

EqualFold reports whether s and t, interpreted as UTF-8 strings, are
equal under simple Unicode case-folding, which is a more general form of
case-insensitivity.

#### [Example]

Code:

```go
fmt.Println(bytes.EqualFold([]byte("Go"), []byte("go")))
```

Output:

```go
true
```

func Fields 
-----------

```go
func Fields(s []byte) [][]byte
```

Fields interprets s as a sequence of UTF-8-encoded code points. It
splits the slice s around each instance of one or more consecutive white
space characters, as defined by unicode.IsSpace, returning a slice of
subslices of s or an empty slice if s contains only white space.

#### [Example]

Code:

```go
fmt.Printf("Fields are: %q", bytes.Fields([]byte("  foo bar  baz   ")))
```

Output:

```go
Fields are: ["foo" "bar" "baz"]
```

func FieldsFunc 
---------------

```go
func FieldsFunc(s []byte, f func(rune) bool) [][]byte
```

FieldsFunc interprets s as a sequence of UTF-8-encoded code points. It
splits the slice s at each run of code points c satisfying f(c) and
returns a slice of subslices of s. If all code points in s satisfy f(c),
or len(s) == 0, an empty slice is returned.

FieldsFunc makes no guarantees about the order in which it calls f(c)
and assumes that f always returns the same value for a given c.

#### [Example]

Code:

```go
f := func(c rune) bool {
    return !unicode.IsLetter(c) && !unicode.IsNumber(c)
}
fmt.Printf("Fields are: %q", bytes.FieldsFunc([]byte("  foo1;bar2,baz3..."), f))
```

Output:

```go
Fields are: ["foo1" "bar2" "baz3"]
```

func HasPrefix 
--------------

```go
func HasPrefix(s, prefix []byte) bool
```

HasPrefix tests whether the byte slice s begins with prefix.

#### [Example]

Code:

```go
fmt.Println(bytes.HasPrefix([]byte("Gopher"), []byte("Go")))
fmt.Println(bytes.HasPrefix([]byte("Gopher"), []byte("C")))
fmt.Println(bytes.HasPrefix([]byte("Gopher"), []byte("")))
```

Output:

```go
true
false
true
```

func HasSuffix 
--------------

```go
func HasSuffix(s, suffix []byte) bool
```

HasSuffix tests whether the byte slice s ends with suffix.

#### [Example]

Code:

```go
fmt.Println(bytes.HasSuffix([]byte("Amigo"), []byte("go")))
fmt.Println(bytes.HasSuffix([]byte("Amigo"), []byte("O")))
fmt.Println(bytes.HasSuffix([]byte("Amigo"), []byte("Ami")))
fmt.Println(bytes.HasSuffix([]byte("Amigo"), []byte("")))
```

Output:

```go
true
false
false
true
```

func Index 
----------

```go
func Index(s, sep []byte) int
```

Index returns the index of the first instance of sep in s, or -1 if sep
is not present in s.

#### [Example]

Code:

```go
fmt.Println(bytes.Index([]byte("chicken"), []byte("ken")))
fmt.Println(bytes.Index([]byte("chicken"), []byte("dmr")))
```

Output:

```go
4
-1
```

func IndexAny 
-------------

```go
func IndexAny(s []byte, chars string) int
```

IndexAny interprets s as a sequence of UTF-8-encoded Unicode code
points. It returns the byte index of the first occurrence in s of any of
the Unicode code points in chars. It returns -1 if chars is empty or if
there is no code point in common.

#### [Example]

Code:

```go
fmt.Println(bytes.IndexAny([]byte("chicken"), "aeiouy"))
fmt.Println(bytes.IndexAny([]byte("crwth"), "aeiouy"))
```

Output:

```go
2
-1
```

func IndexByte 
--------------

```go
func IndexByte(b []byte, c byte) int
```

IndexByte returns the index of the first instance of c in b, or -1 if c
is not present in b.

#### [Example]

Code:

```go
fmt.Println(bytes.IndexByte([]byte("chicken"), byte('k')))
fmt.Println(bytes.IndexByte([]byte("chicken"), byte('g')))
```

Output:

```go
4
-1
```

func IndexFunc 
--------------

```go
func IndexFunc(s []byte, f func(r rune) bool) int
```

IndexFunc interprets s as a sequence of UTF-8-encoded code points. It
returns the byte index in s of the first Unicode code point satisfying
f(c), or -1 if none do.

#### [Example]

Code:

```go
f := func(c rune) bool {
    return unicode.Is(unicode.Han, c)
}
fmt.Println(bytes.IndexFunc([]byte("Hello, 世界"), f))
fmt.Println(bytes.IndexFunc([]byte("Hello, world"), f))
```

Output:

```go
7
-1
```

func IndexRune 
--------------

```go
func IndexRune(s []byte, r rune) int
```

IndexRune interprets s as a sequence of UTF-8-encoded code points. It
returns the byte index of the first occurrence in s of the given rune.
It returns -1 if rune is not present in s. If r is utf8.RuneError, it
returns the first instance of any invalid UTF-8 byte sequence.

#### [Example]

Code:

```go
fmt.Println(bytes.IndexRune([]byte("chicken"), 'k'))
fmt.Println(bytes.IndexRune([]byte("chicken"), 'd'))
```

Output:

```go
4
-1
```

func Join 
---------

```go
func Join(s [][]byte, sep []byte) []byte
```

Join concatenates the elements of s to create a new byte slice. The
separator sep is placed between elements in the resulting slice.

#### [Example]

Code:

```go
s := [][]byte{[]byte("foo"), []byte("bar"), []byte("baz")}
fmt.Printf("%s", bytes.Join(s, []byte(", ")))
```

Output:

```go
foo, bar, baz
```

func LastIndex 
--------------

```go
func LastIndex(s, sep []byte) int
```

LastIndex returns the index of the last instance of sep in s, or -1 if
sep is not present in s.

#### [Example]

Code:

```go
fmt.Println(bytes.Index([]byte("go gopher"), []byte("go")))
fmt.Println(bytes.LastIndex([]byte("go gopher"), []byte("go")))
fmt.Println(bytes.LastIndex([]byte("go gopher"), []byte("rodent")))
```

Output:

```go
0
3
-1
```

func LastIndexAny 
-----------------

```go
func LastIndexAny(s []byte, chars string) int
```

LastIndexAny interprets s as a sequence of UTF-8-encoded Unicode code
points. It returns the byte index of the last occurrence in s of any of
the Unicode code points in chars. It returns -1 if chars is empty or if
there is no code point in common.

#### [Example]

Code:

```go
fmt.Println(bytes.LastIndexAny([]byte("go gopher"), "MüQp"))
fmt.Println(bytes.LastIndexAny([]byte("go 地鼠"), "地大"))
fmt.Println(bytes.LastIndexAny([]byte("go gopher"), "z,!."))
```

Output:

```go
5
3
-1
```

func LastIndexByte 
-------------------------------------------------

```go
func LastIndexByte(s []byte, c byte) int
```

LastIndexByte returns the index of the last instance of c in s, or -1 if
c is not present in s.

#### [Example]

Code:

```go
fmt.Println(bytes.LastIndexByte([]byte("go gopher"), byte('g')))
fmt.Println(bytes.LastIndexByte([]byte("go gopher"), byte('r')))
fmt.Println(bytes.LastIndexByte([]byte("go gopher"), byte('z')))
```

Output:

```go
3
8
-1
```

func LastIndexFunc 
------------------

```go
func LastIndexFunc(s []byte, f func(r rune) bool) int
```

LastIndexFunc interprets s as a sequence of UTF-8-encoded code points.
It returns the byte index in s of the last Unicode code point satisfying
f(c), or -1 if none do.

#### [Example]

Code:

```go
fmt.Println(bytes.LastIndexFunc([]byte("go gopher!"), unicode.IsLetter))
fmt.Println(bytes.LastIndexFunc([]byte("go gopher!"), unicode.IsPunct))
fmt.Println(bytes.LastIndexFunc([]byte("go gopher!"), unicode.IsNumber))
```

Output:

```go
8
9
-1
```

func Map 
--------

```go
func Map(mapping func(r rune) rune, s []byte) []byte
```

Map returns a copy of the byte slice s with all its characters modified
according to the mapping function. If mapping returns a negative value,
the character is dropped from the byte slice with no replacement. The
characters in s and the output are interpreted as UTF-8-encoded code
points.

#### [Example]

Code:

```go
rot13 := func(r rune) rune {
    switch {
    case r >= 'A' && r <= 'Z':
        return 'A' + (r-'A'+13)%26
    case r >= 'a' && r <= 'z':
        return 'a' + (r-'a'+13)%26
    }
    return r
}
fmt.Printf("%s\n", bytes.Map(rot13, []byte("'Twas brillig and the slithy gopher...")))
```

Output:

```go
'Gjnf oevyyvt naq gur fyvgul tbcure...
```

func Repeat 
-----------

```go
func Repeat(b []byte, count int) []byte
```

Repeat returns a new byte slice consisting of count copies of b.

It panics if count is negative or if the result of (len(b) \* count)
overflows.

#### [Example]

Code:

```go
fmt.Printf("ba%s", bytes.Repeat([]byte("na"), 2))
```

Output:

```go
banana
```

func Replace 
------------

```go
func Replace(s, old, new []byte, n int) []byte
```

Replace returns a copy of the slice s with the first n non-overlapping
instances of old replaced by new. If old is empty, it matches at the
beginning of the slice and after each UTF-8 sequence, yielding up to k+1
replacements for a k-rune slice. If n \< 0, there is no limit on the
number of replacements.

#### [Example]

Code:

```go
fmt.Printf("%s\n", bytes.Replace([]byte("oink oink oink"), []byte("k"), []byte("ky"), 2))
fmt.Printf("%s\n", bytes.Replace([]byte("oink oink oink"), []byte("oink"), []byte("moo"), -1))
```

Output:

```go
oinky oinky oink
moo moo moo
```

func ReplaceAll 
------------------------------------------------

```go
func ReplaceAll(s, old, new []byte) []byte
```

ReplaceAll returns a copy of the slice s with all non-overlapping
instances of old replaced by new. If old is empty, it matches at the
beginning of the slice and after each UTF-8 sequence, yielding up to k+1
replacements for a k-rune slice.

#### [Example]

Code:

```go
fmt.Printf("%s\n", bytes.ReplaceAll([]byte("oink oink oink"), []byte("oink"), []byte("moo")))
```

Output:

```go
moo moo moo
```

func Runes 
----------

```go
func Runes(s []byte) []rune
```

Runes interprets s as a sequence of UTF-8-encoded code points. It
returns a slice of runes (Unicode code points) equivalent to s.

#### [Example]

Code:

```go
rs := bytes.Runes([]byte("go gopher"))
for _, r := range rs {
    fmt.Printf("%#U\n", r)
}
```

Output:

```go
U+0067 'g'
U+006F 'o'
U+0020 ' '
U+0067 'g'
U+006F 'o'
U+0070 'p'
U+0068 'h'
U+0065 'e'
U+0072 'r'
```

func Split 
----------

```go
func Split(s, sep []byte) [][]byte
```

Split slices s into all subslices separated by sep and returns a slice
of the subslices between those separators. If sep is empty, Split splits
after each UTF-8 sequence. It is equivalent to SplitN with a count of
-1.

To split around the first instance of a separator, see Cut.

#### [Example]

Code:

```go
fmt.Printf("%q\n", bytes.Split([]byte("a,b,c"), []byte(",")))
fmt.Printf("%q\n", bytes.Split([]byte("a man a plan a canal panama"), []byte("a ")))
fmt.Printf("%q\n", bytes.Split([]byte(" xyz "), []byte("")))
fmt.Printf("%q\n", bytes.Split([]byte(""), []byte("Bernardo O'Higgins")))
```

Output:

```go
["a" "b" "c"]
["" "man " "plan " "canal panama"]
[" " "x" "y" "z" " "]
[""]
```

func SplitAfter 
---------------

```go
func SplitAfter(s, sep []byte) [][]byte
```

SplitAfter slices s into all subslices after each instance of sep and
returns a slice of those subslices. If sep is empty, SplitAfter splits
after each UTF-8 sequence. It is equivalent to SplitAfterN with a count
of -1.

#### [Example]

Code:

```go
fmt.Printf("%q\n", bytes.SplitAfter([]byte("a,b,c"), []byte(",")))
```

Output:

```go
["a," "b," "c"]
```

func SplitAfterN 
----------------

```go
func SplitAfterN(s, sep []byte, n int) [][]byte
```

SplitAfterN slices s into subslices after each instance of sep and
returns a slice of those subslices. If sep is empty, SplitAfterN splits
after each UTF-8 sequence. The count determines the number of subslices
to return:

```go
n > 0: at most n subslices; the last subslice will be the unsplit remainder.
n == 0: the result is nil (zero subslices)
n < 0: all subslices
```

#### [Example]

Code:

```go
fmt.Printf("%q\n", bytes.SplitAfterN([]byte("a,b,c"), []byte(","), 2))
```

Output:

```go
["a," "b,c"]
```

func SplitN 
-----------

```go
func SplitN(s, sep []byte, n int) [][]byte
```

SplitN slices s into subslices separated by sep and returns a slice of
the subslices between those separators. If sep is empty, SplitN splits
after each UTF-8 sequence. The count determines the number of subslices
to return:

```go
n > 0: at most n subslices; the last subslice will be the unsplit remainder.
n == 0: the result is nil (zero subslices)
n < 0: all subslices
```

To split around the first instance of a separator, see Cut.

#### [Example]

Code:

```go
fmt.Printf("%q\n", bytes.SplitN([]byte("a,b,c"), []byte(","), 2))
z := bytes.SplitN([]byte("a,b,c"), []byte(","), 0)
fmt.Printf("%q (nil = %v)\n", z, z == nil)
```

Output:

```go
["a" "b,c"]
[] (nil = true)
```

func Title 
----------

```go
func Title(s []byte) []byte
```

Title treats s as UTF-8-encoded bytes and returns a copy with all
Unicode letters that begin words mapped to their title case.

Deprecated: The rule Title uses for word boundaries does not handle
Unicode punctuation properly. Use golang.org/x/text/cases instead.

#### [Example]

Code:

```go
fmt.Printf("%s", bytes.Title([]byte("her royal highness")))
```

Output:

```go
Her Royal Highness
```

func ToLower 
------------

```go
func ToLower(s []byte) []byte
```

ToLower returns a copy of the byte slice s with all Unicode letters
mapped to their lower case.

#### [Example]

Code:

```go
fmt.Printf("%s", bytes.ToLower([]byte("Gopher")))
```

Output:

```go
gopher
```

func ToLowerSpecial 
-------------------

```go
func ToLowerSpecial(c unicode.SpecialCase, s []byte) []byte
```

ToLowerSpecial treats s as UTF-8-encoded bytes and returns a copy with
all the Unicode letters mapped to their lower case, giving priority to
the special casing rules.

#### [Example]

Code:

```go
str := []byte("AHOJ VÝVOJÁRİ GOLANG")
totitle := bytes.ToLowerSpecial(unicode.AzeriCase, str)
fmt.Println("Original : " + string(str))
fmt.Println("ToLower : " + string(totitle))
```

Output:

```go
Original : AHOJ VÝVOJÁRİ GOLANG
ToLower : ahoj vývojári golang
```

func ToTitle 
------------

```go
func ToTitle(s []byte) []byte
```

ToTitle treats s as UTF-8-encoded bytes and returns a copy with all the
Unicode letters mapped to their title case.

#### [Example]

Code:

```go
fmt.Printf("%s\n", bytes.ToTitle([]byte("loud noises")))
fmt.Printf("%s\n", bytes.ToTitle([]byte("хлеб")))
```

Output:

```go
LOUD NOISES
ХЛЕБ
```

func ToTitleSpecial 
-------------------

```go
func ToTitleSpecial(c unicode.SpecialCase, s []byte) []byte
```

ToTitleSpecial treats s as UTF-8-encoded bytes and returns a copy with
all the Unicode letters mapped to their title case, giving priority to
the special casing rules.

#### [Example]

Code:

```go
str := []byte("ahoj vývojári golang")
totitle := bytes.ToTitleSpecial(unicode.AzeriCase, str)
fmt.Println("Original : " + string(str))
fmt.Println("ToTitle : " + string(totitle))
```

Output:

```go
Original : ahoj vývojári golang
ToTitle : AHOJ VÝVOJÁRİ GOLANG
```

func ToUpper 
------------

```go
func ToUpper(s []byte) []byte
```

ToUpper returns a copy of the byte slice s with all Unicode letters
mapped to their upper case.

#### [Example]

Code:

```go
fmt.Printf("%s", bytes.ToUpper([]byte("Gopher")))
```

Output:

```go
GOPHER
```

func ToUpperSpecial 
-------------------

```go
func ToUpperSpecial(c unicode.SpecialCase, s []byte) []byte
```

ToUpperSpecial treats s as UTF-8-encoded bytes and returns a copy with
all the Unicode letters mapped to their upper case, giving priority to
the special casing rules.

#### [Example]

Code:

```go
str := []byte("ahoj vývojári golang")
totitle := bytes.ToUpperSpecial(unicode.AzeriCase, str)
fmt.Println("Original : " + string(str))
fmt.Println("ToUpper : " + string(totitle))
```

Output:

```go
Original : ahoj vývojári golang
ToUpper : AHOJ VÝVOJÁRİ GOLANG
```

func ToValidUTF8 
-------------------------------------------------

```go
func ToValidUTF8(s, replacement []byte) []byte
```

ToValidUTF8 treats s as UTF-8-encoded bytes and returns a copy with each
run of bytes representing invalid UTF-8 replaced with the bytes in
replacement, which may be empty.

#### [Example]

Code:

```go
fmt.Printf("%s\n", bytes.ToValidUTF8([]byte("abc"), []byte("\uFFFD")))
fmt.Printf("%s\n", bytes.ToValidUTF8([]byte("a\xffb\xC0\xAFc\xff"), []byte("")))
fmt.Printf("%s\n", bytes.ToValidUTF8([]byte("\xed\xa0\x80"), []byte("abc")))
```

Output:

```go
abc
abc
abc
```

func Trim 
---------

```go
func Trim(s []byte, cutset string) []byte
```

Trim returns a subslice of s by slicing off all leading and trailing
UTF-8-encoded code points contained in cutset.

#### [Example]

Code:

```go
fmt.Printf("[%q]", bytes.Trim([]byte(" !!! Achtung! Achtung! !!! "), "! "))
```

Output:

```go
["Achtung! Achtung"]
```

func TrimFunc 
-------------

```go
func TrimFunc(s []byte, f func(r rune) bool) []byte
```

TrimFunc returns a subslice of s by slicing off all leading and trailing
UTF-8-encoded code points c that satisfy f(c).

#### [Example]

Code:

```go
fmt.Println(string(bytes.TrimFunc([]byte("go-gopher!"), unicode.IsLetter)))
fmt.Println(string(bytes.TrimFunc([]byte("\"go-gopher!\""), unicode.IsLetter)))
fmt.Println(string(bytes.TrimFunc([]byte("go-gopher!"), unicode.IsPunct)))
fmt.Println(string(bytes.TrimFunc([]byte("1234go-gopher!567"), unicode.IsNumber)))
```

Output:

```go
-gopher!
"go-gopher!"
go-gopher
go-gopher!
```

func TrimLeft 
-------------

```go
func TrimLeft(s []byte, cutset string) []byte
```

TrimLeft returns a subslice of s by slicing off all leading
UTF-8-encoded code points contained in cutset.

#### [Example]

Code:

```go
fmt.Print(string(bytes.TrimLeft([]byte("453gopher8257"), "0123456789")))
```

Output:

```go
gopher8257
```

func TrimLeftFunc 
-----------------

```go
func TrimLeftFunc(s []byte, f func(r rune) bool) []byte
```

TrimLeftFunc treats s as UTF-8-encoded bytes and returns a subslice of s
by slicing off all leading UTF-8-encoded code points c that satisfy
f(c).

#### [Example]

Code:

```go
fmt.Println(string(bytes.TrimLeftFunc([]byte("go-gopher"), unicode.IsLetter)))
fmt.Println(string(bytes.TrimLeftFunc([]byte("go-gopher!"), unicode.IsPunct)))
fmt.Println(string(bytes.TrimLeftFunc([]byte("1234go-gopher!567"), unicode.IsNumber)))
```

Output:

```go
-gopher
go-gopher!
go-gopher!567
```

func TrimPrefix 
----------------------------------------------

```go
func TrimPrefix(s, prefix []byte) []byte
```

TrimPrefix returns s without the provided leading prefix string. If s
doesn\'t start with prefix, s is returned unchanged.

#### [Example]

Code:

```go
var b = []byte("Goodbye,, world!")
b = bytes.TrimPrefix(b, []byte("Goodbye,"))
b = bytes.TrimPrefix(b, []byte("See ya,"))
fmt.Printf("Hello%s", b)
```

Output:

```go
Hello, world!
```

func TrimRight 
--------------

```go
func TrimRight(s []byte, cutset string) []byte
```

TrimRight returns a subslice of s by slicing off all trailing
UTF-8-encoded code points that are contained in cutset.

#### [Example]

Code:

```go
fmt.Print(string(bytes.TrimRight([]byte("453gopher8257"), "0123456789")))
```

Output:

```go
453gopher
```

func TrimRightFunc 
------------------

```go
func TrimRightFunc(s []byte, f func(r rune) bool) []byte
```

TrimRightFunc returns a subslice of s by slicing off all trailing
UTF-8-encoded code points c that satisfy f(c).

#### [Example]

Code:

```go
fmt.Println(string(bytes.TrimRightFunc([]byte("go-gopher"), unicode.IsLetter)))
fmt.Println(string(bytes.TrimRightFunc([]byte("go-gopher!"), unicode.IsPunct)))
fmt.Println(string(bytes.TrimRightFunc([]byte("1234go-gopher!567"), unicode.IsNumber)))
```

Output:

```go
go-
go-gopher
1234go-gopher!
```

func TrimSpace 
--------------

```go
func TrimSpace(s []byte) []byte
```

TrimSpace returns a subslice of s by slicing off all leading and
trailing white space, as defined by Unicode.

#### [Example]

Code:

```go
fmt.Printf("%s", bytes.TrimSpace([]byte(" \t\n a lone gopher \n\t\r\n")))
```

Output:

```go
a lone gopher
```

func TrimSuffix 
----------------------------------------------

```go
func TrimSuffix(s, suffix []byte) []byte
```

TrimSuffix returns s without the provided trailing suffix string. If s
doesn\'t end with suffix, s is returned unchanged.

#### [Example]

Code:

```go
var b = []byte("Hello, goodbye, etc!")
b = bytes.TrimSuffix(b, []byte("goodbye, etc!"))
b = bytes.TrimSuffix(b, []byte("gopher"))
b = append(b, bytes.TrimSuffix([]byte("world!"), []byte("x!"))...)
os.Stdout.Write(b)
```

Output:

```go
Hello, world!
```

type Buffer 
-----------

A Buffer is a variable-sized buffer of bytes with Read and Write
methods. The zero value for Buffer is an empty buffer ready to use.

```go
type Buffer struct {
    // contains filtered or unexported fields
}
```

#### [Example]

Code:

```go
var b bytes.Buffer // A Buffer needs no initialization.
b.Write([]byte("Hello "))
fmt.Fprintf(&b, "world!")
b.WriteTo(os.Stdout)
```

Output:

```go
Hello world!
```

#### [Example (Reader)]

Code:

```go
// A Buffer can turn a string or a []byte into an io.Reader.
buf := bytes.NewBufferString("R29waGVycyBydWxlIQ==")
dec := base64.NewDecoder(base64.StdEncoding, buf)
io.Copy(os.Stdout, dec)
```

Output:

```go
Gophers rule!
```

### func NewBuffer 

```go
func NewBuffer(buf []byte) *Buffer
```

NewBuffer creates and initializes a new Buffer using buf as its initial
contents. The new Buffer takes ownership of buf, and the caller should
not use buf after this call. NewBuffer is intended to prepare a Buffer
to read existing data. It can also be used to set the initial size of
the internal buffer for writing. To do that, buf should have the desired
capacity but a length of zero.

In most cases, new(Buffer) (or just declaring a Buffer variable) is
sufficient to initialize a Buffer.

### func NewBufferString 

```go
func NewBufferString(s string) *Buffer
```

NewBufferString creates and initializes a new Buffer using string s as
its initial contents. It is intended to prepare a buffer to read an
existing string.

In most cases, new(Buffer) (or just declaring a Buffer variable) is
sufficient to initialize a Buffer.

### func (\*Buffer) Available 

```go
func (b *Buffer) Available() int
```

Available returns how many bytes are unused in the buffer.

### func (\*Buffer) AvailableBuffer 

```go
func (b *Buffer) AvailableBuffer() []byte
```

AvailableBuffer returns an empty buffer with b.Available() capacity.
This buffer is intended to be appended to and passed to an immediately
succeeding Write call. The buffer is only valid until the next write
operation on b.

#### [Example]

Code:

```go
var buf bytes.Buffer
for i := 0; i < 4; i++ {
    b := buf.AvailableBuffer()
    b = strconv.AppendInt(b, int64(i), 10)
    b = append(b, ' ')
    buf.Write(b)
}
os.Stdout.Write(buf.Bytes())
```

Output:

```go
0 1 2 3
```

### func (\*Buffer) Bytes 

```go
func (b *Buffer) Bytes() []byte
```

Bytes returns a slice of length b.Len() holding the unread portion of
the buffer. The slice is valid for use only until the next buffer
modification (that is, only until the next call to a method like Read,
Write, Reset, or Truncate). The slice aliases the buffer content at
least until the next buffer modification, so immediate changes to the
slice will affect the result of future reads.

#### [Example]

Code:

```go
buf := bytes.Buffer{}
buf.Write([]byte{'h', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd'})
os.Stdout.Write(buf.Bytes())
```

Output:

```go
hello world
```

### func (\*Buffer) Cap 

```go
func (b *Buffer) Cap() int
```

Cap returns the capacity of the buffer\'s underlying byte slice, that
is, the total space allocated for the buffer\'s data.

#### [Example]

Code:

```go
buf1 := bytes.NewBuffer(make([]byte, 10))
buf2 := bytes.NewBuffer(make([]byte, 0, 10))
fmt.Println(buf1.Cap())
fmt.Println(buf2.Cap())
```

Output:

```go
10
10
```

### func (\*Buffer) Grow 

```go
func (b *Buffer) Grow(n int)
```

Grow grows the buffer\'s capacity, if necessary, to guarantee space for
another n bytes. After Grow(n), at least n bytes can be written to the
buffer without another allocation. If n is negative, Grow will panic. If
the buffer can\'t grow it will panic with ErrTooLarge.

#### [Example]

Code:

```go
var b bytes.Buffer
b.Grow(64)
bb := b.Bytes()
b.Write([]byte("64 bytes or fewer"))
fmt.Printf("%q", bb[:b.Len()])
```

Output:

```go
"64 bytes or fewer"
```

### func (\*Buffer) Len 

```go
func (b *Buffer) Len() int
```

Len returns the number of bytes of the unread portion of the buffer;
b.Len() == len(b.Bytes()).

#### [Example]

Code:

```go
var b bytes.Buffer
b.Grow(64)
b.Write([]byte("abcde"))
fmt.Printf("%d", b.Len())
```

Output:

```go
5
```

### func (\*Buffer) Next 

```go
func (b *Buffer) Next(n int) []byte
```

Next returns a slice containing the next n bytes from the buffer,
advancing the buffer as if the bytes had been returned by Read. If there
are fewer than n bytes in the buffer, Next returns the entire buffer.
The slice is only valid until the next call to a read or write method.

#### [Example]

Code:

```go
var b bytes.Buffer
b.Grow(64)
b.Write([]byte("abcde"))
fmt.Printf("%s\n", string(b.Next(2)))
fmt.Printf("%s\n", string(b.Next(2)))
fmt.Printf("%s", string(b.Next(2)))
```

Output:

```go
ab
cd
e
```

### func (\*Buffer) Read 

```go
func (b *Buffer) Read(p []byte) (n int, err error)
```

Read reads the next len(p) bytes from the buffer or until the buffer is
drained. The return value n is the number of bytes read. If the buffer
has no data to return, err is io.EOF (unless len(p) is zero); otherwise
it is nil.

#### [Example]

Code:

```go
var b bytes.Buffer
b.Grow(64)
b.Write([]byte("abcde"))
rdbuf := make([]byte, 1)
n, err := b.Read(rdbuf)
if err != nil {
    panic(err)
}
fmt.Println(n)
fmt.Println(b.String())
fmt.Println(string(rdbuf))
// Output
// 1
// bcde
// a
```

### func (\*Buffer) ReadByte 

```go
func (b *Buffer) ReadByte() (byte, error)
```

ReadByte reads and returns the next byte from the buffer. If no byte is
available, it returns error io.EOF.

#### [Example]

Code:

```go
var b bytes.Buffer
b.Grow(64)
b.Write([]byte("abcde"))
c, err := b.ReadByte()
if err != nil {
    panic(err)
}
fmt.Println(c)
fmt.Println(b.String())
// Output
// 97
// bcde
```

### func (\*Buffer) ReadBytes 

```go
func (b *Buffer) ReadBytes(delim byte) (line []byte, err error)
```

ReadBytes reads until the first occurrence of delim in the input,
returning a slice containing the data up to and including the delimiter.
If ReadBytes encounters an error before finding a delimiter, it returns
the data read before the error and the error itself (often io.EOF).
ReadBytes returns err != nil if and only if the returned data does not
end in delim.

### func (\*Buffer) ReadFrom 

```go
func (b *Buffer) ReadFrom(r io.Reader) (n int64, err error)
```

ReadFrom reads data from r until EOF and appends it to the buffer,
growing the buffer as needed. The return value n is the number of bytes
read. Any error except io.EOF encountered during the read is also
returned. If the buffer becomes too large, ReadFrom will panic with
ErrTooLarge.

### func (\*Buffer) ReadRune 

```go
func (b *Buffer) ReadRune() (r rune, size int, err error)
```

ReadRune reads and returns the next UTF-8-encoded Unicode code point
from the buffer. If no bytes are available, the error returned is
io.EOF. If the bytes are an erroneous UTF-8 encoding, it consumes one
byte and returns U+FFFD, 1.

### func (\*Buffer) ReadString 

```go
func (b *Buffer) ReadString(delim byte) (line string, err error)
```

ReadString reads until the first occurrence of delim in the input,
returning a string containing the data up to and including the
delimiter. If ReadString encounters an error before finding a delimiter,
it returns the data read before the error and the error itself (often
io.EOF). ReadString returns err != nil if and only if the returned data
does not end in delim.

### func (\*Buffer) Reset 

```go
func (b *Buffer) Reset()
```

Reset resets the buffer to be empty, but it retains the underlying
storage for use by future writes. Reset is the same as Truncate(0).

### func (\*Buffer) String 

```go
func (b *Buffer) String() string
```

String returns the contents of the unread portion of the buffer as a
string. If the Buffer is a nil pointer, it returns \"\<nil\>\".

To build strings more efficiently, see the strings.Builder type.

### func (\*Buffer) Truncate 

```go
func (b *Buffer) Truncate(n int)
```

Truncate discards all but the first n unread bytes from the buffer but
continues to use the same allocated storage. It panics if n is negative
or greater than the length of the buffer.

### func (\*Buffer) UnreadByte 

```go
func (b *Buffer) UnreadByte() error
```

UnreadByte unreads the last byte returned by the most recent successful
read operation that read at least one byte. If a write has happened
since the last read, if the last read returned an error, or if the read
read zero bytes, UnreadByte returns an error.

### func (\*Buffer) UnreadRune 

```go
func (b *Buffer) UnreadRune() error
```

UnreadRune unreads the last rune returned by ReadRune. If the most
recent read or write operation on the buffer was not a successful
ReadRune, UnreadRune returns an error. (In this regard it is stricter
than UnreadByte, which will unread the last byte from any read
operation.)

### func (\*Buffer) Write 

```go
func (b *Buffer) Write(p []byte) (n int, err error)
```

Write appends the contents of p to the buffer, growing the buffer as
needed. The return value n is the length of p; err is always nil. If the
buffer becomes too large, Write will panic with ErrTooLarge.

### func (\*Buffer) WriteByte 

```go
func (b *Buffer) WriteByte(c byte) error
```

WriteByte appends the byte c to the buffer, growing the buffer as
needed. The returned error is always nil, but is included to match
bufio.Writer\'s WriteByte. If the buffer becomes too large, WriteByte
will panic with ErrTooLarge.

### func (\*Buffer) WriteRune 

```go
func (b *Buffer) WriteRune(r rune) (n int, err error)
```

WriteRune appends the UTF-8 encoding of Unicode code point r to the
buffer, returning its length and an error, which is always nil but is
included to match bufio.Writer\'s WriteRune. The buffer is grown as
needed; if it becomes too large, WriteRune will panic with ErrTooLarge.

### func (\*Buffer) WriteString 

```go
func (b *Buffer) WriteString(s string) (n int, err error)
```

WriteString appends the contents of s to the buffer, growing the buffer
as needed. The return value n is the length of s; err is always nil. If
the buffer becomes too large, WriteString will panic with ErrTooLarge.

### func (\*Buffer) WriteTo 

```go
func (b *Buffer) WriteTo(w io.Writer) (n int64, err error)
```

WriteTo writes data to w until the buffer is drained or an error occurs.
The return value n is the number of bytes written; it always fits into
an int, but it is int64 to match the io.WriterTo interface. Any error
encountered during the write is also returned.

type Reader 
-----------

A Reader implements the io.Reader, io.ReaderAt, io.WriterTo, io.Seeker,
io.ByteScanner, and io.RuneScanner interfaces by reading from a byte
slice. Unlike a Buffer, a Reader is read-only and supports seeking. The
zero value for Reader operates like a Reader of an empty slice.

```go
type Reader struct {
    // contains filtered or unexported fields
}
```

### func NewReader 

```go
func NewReader(b []byte) *Reader
```

NewReader returns a new Reader reading from b.

### func (\*Reader) Len 

```go
func (r *Reader) Len() int
```

Len returns the number of bytes of the unread portion of the slice.

#### [Example]

Code:

```go
fmt.Println(bytes.NewReader([]byte("Hi!")).Len())
fmt.Println(bytes.NewReader([]byte("こんにちは!")).Len())
```

Output:

```go
3
16
```

### func (\*Reader) Read 

```go
func (r *Reader) Read(b []byte) (n int, err error)
```

Read implements the io.Reader interface.

### func (\*Reader) ReadAt 

```go
func (r *Reader) ReadAt(b []byte, off int64) (n int, err error)
```

ReadAt implements the io.ReaderAt interface.

### func (\*Reader) ReadByte 

```go
func (r *Reader) ReadByte() (byte, error)
```

ReadByte implements the io.ByteReader interface.

### func (\*Reader) ReadRune 

```go
func (r *Reader) ReadRune() (ch rune, size int, err error)
```

ReadRune implements the io.RuneReader interface.

### func (\*Reader) Reset 

```go
func (r *Reader) Reset(b []byte)
```

Reset resets the Reader to be reading from b.

### func (\*Reader) Seek 

```go
func (r *Reader) Seek(offset int64, whence int) (int64, error)
```

Seek implements the io.Seeker interface.

### func (\*Reader) Size 

```go
func (r *Reader) Size() int64
```

Size returns the original length of the underlying byte slice. Size is
the number of bytes available for reading via ReadAt. The result is
unaffected by any method calls except Reset.

### func (\*Reader) UnreadByte 

```go
func (r *Reader) UnreadByte() error
```

UnreadByte complements ReadByte in implementing the io.ByteScanner
interface.

### func (\*Reader) UnreadRune 

```go
func (r *Reader) UnreadRune() error
```

UnreadRune complements ReadRune in implementing the io.RuneScanner
interface.

### func (\*Reader) WriteTo 

```go
func (r *Reader) WriteTo(w io.Writer) (n int64, err error)
```

WriteTo implements the io.WriterTo interface.

 
© Google, Inc.\
Licensed under the Creative Commons Attribution License 3.0.\
https://golang.org/pkg/bytes/>


Package dwarf
=============

-   `import "debug/dwarf"`
-   [Overview](#pkg-overview)
-   [Index](#pkg-index)

Overview 
--------

Package dwarf provides access to DWARF debugging information loaded from
executable files, as defined in the DWARF 2.0 Standard at
https://dwarfstd.org/doc/dwarf-2.0.0.pdf>.

### Security 

This package is not designed to be hardened against adversarial inputs,
and is outside the scope of https://go.dev/security/policy>. In
particular, only basic validation is done when parsing object files. As
such, care should be taken when parsing untrusted inputs, as parsing
malformed files may consume significant resources, or cause panics.

Index 
-----

-   [Variables](#pkg-variables)
-   [type AddrType](#AddrType)
-   [type ArrayType](#ArrayType)
-   [func (t \*ArrayType) Size() int64](#ArrayType.Size)
-   [func (t \*ArrayType) String() string](#ArrayType.String)
-   [type Attr](#Attr)
-   [func (a Attr) GoString() string](#Attr.GoString)
-   [func (i Attr) String() string](#Attr.String)
-   [type BasicType](#BasicType)
-   [func (b \*BasicType) Basic() \*BasicType](#BasicType.Basic)
-   [func (t \*BasicType) String() string](#BasicType.String)
-   [type BoolType](#BoolType)
-   [type CharType](#CharType)
-   [type Class](#Class)
-   [func (i Class) GoString() string](#Class.GoString)
-   [func (i Class) String() string](#Class.String)
-   [type CommonType](#CommonType)
-   [func (c \*CommonType) Common() \*CommonType](#CommonType.Common)
-   [func (c \*CommonType) Size() int64](#CommonType.Size)
-   [type ComplexType](#ComplexType)
-   [type Data](#Data)
-   [func New(abbrev, aranges, frame, info, line, pubnames, ranges, str
    \[\]byte) (\*Data, error)](#New)
-   [func (d \*Data) AddSection(name string, contents \[\]byte)
    error](#Data.AddSection)
-   [func (d \*Data) AddTypes(name string, types \[\]byte)
    error](#Data.AddTypes)
-   [func (d \*Data) LineReader(cu \*Entry) (\*LineReader,
    error)](#Data.LineReader)
-   [func (d \*Data) Ranges(e \*Entry) (\[\]\[2\]uint64,
    error)](#Data.Ranges)
-   [func (d \*Data) Reader() \*Reader](#Data.Reader)
-   [func (d \*Data) Type(off Offset) (Type, error)](#Data.Type)
-   [type DecodeError](#DecodeError)
-   [func (e DecodeError) Error() string](#DecodeError.Error)
-   [type DotDotDotType](#DotDotDotType)
-   [func (t \*DotDotDotType) String() string](#DotDotDotType.String)
-   [type Entry](#Entry)
-   [func (e \*Entry) AttrField(a Attr) \*Field](#Entry.AttrField)
-   [func (e \*Entry) Val(a Attr) any](#Entry.Val)
-   [type EnumType](#EnumType)
-   [func (t \*EnumType) String() string](#EnumType.String)
-   [type EnumValue](#EnumValue)
-   [type Field](#Field)
-   [type FloatType](#FloatType)
-   [type FuncType](#FuncType)
-   [func (t \*FuncType) String() string](#FuncType.String)
-   [type IntType](#IntType)
-   [type LineEntry](#LineEntry)
-   [type LineFile](#LineFile)
-   [type LineReader](#LineReader)
-   [func (r \*LineReader) Files() \[\]\*LineFile](#LineReader.Files)
-   [func (r \*LineReader) Next(entry \*LineEntry)
    error](#LineReader.Next)
-   [func (r \*LineReader) Reset()](#LineReader.Reset)
-   [func (r \*LineReader) Seek(pos LineReaderPos)](#LineReader.Seek)
-   [func (r \*LineReader) SeekPC(pc uint64, entry \*LineEntry)
    error](#LineReader.SeekPC)
-   [func (r \*LineReader) Tell() LineReaderPos](#LineReader.Tell)
-   [type LineReaderPos](#LineReaderPos)
-   [type Offset](#Offset)
-   [type PtrType](#PtrType)
-   [func (t \*PtrType) String() string](#PtrType.String)
-   [type QualType](#QualType)
-   [func (t \*QualType) Size() int64](#QualType.Size)
-   [func (t \*QualType) String() string](#QualType.String)
-   [type Reader](#Reader)
-   [func (r \*Reader) AddressSize() int](#Reader.AddressSize)
-   [func (r \*Reader) ByteOrder() binary.ByteOrder](#Reader.ByteOrder)
-   [func (r \*Reader) Next() (\*Entry, error)](#Reader.Next)
-   [func (r \*Reader) Seek(off Offset)](#Reader.Seek)
-   [func (r \*Reader) SeekPC(pc uint64) (\*Entry,
    error)](#Reader.SeekPC)
-   [func (r \*Reader) SkipChildren()](#Reader.SkipChildren)
-   [type StructField](#StructField)
-   [type StructType](#StructType)
-   [func (t \*StructType) Defn() string](#StructType.Defn)
-   [func (t \*StructType) String() string](#StructType.String)
-   [type Tag](#Tag)
-   [func (t Tag) GoString() string](#Tag.GoString)
-   [func (i Tag) String() string](#Tag.String)
-   [type Type](#Type)
-   [type TypedefType](#TypedefType)
-   [func (t \*TypedefType) Size() int64](#TypedefType.Size)
-   [func (t \*TypedefType) String() string](#TypedefType.String)
-   [type UcharType](#UcharType)
-   [type UintType](#UintType)
-   [type UnspecifiedType](#UnspecifiedType)
-   [type UnsupportedType](#UnsupportedType)
-   [func (t \*UnsupportedType) String()
    string](#UnsupportedType.String)
-   [type VoidType](#VoidType)
-   [func (t \*VoidType) String() string](#VoidType.String)

### Package files

attr\_string.go buf.go class\_string.go const.go entry.go line.go
open.go tag\_string.go type.go typeunit.go unit.go

Variables 
---------

ErrUnknownPC is the error returned by LineReader.ScanPC when the seek PC
is not covered by any entry in the line table.

```go
var ErrUnknownPC = errors.New("ErrUnknownPC")
```

type AddrType 
-------------

An AddrType represents a machine address type.

```go
type AddrType struct {
    BasicType
}
```

type ArrayType 
--------------

An ArrayType represents a fixed size array type.

```go
type ArrayType struct {
    CommonType
    Type          Type
    StrideBitSize int64 // if > 0, number of bits to hold each element
    Count         int64 // if == -1, an incomplete array, like char x[].
}
```

### func (\*ArrayType) Size 

```go
func (t *ArrayType) Size() int64
```

### func (\*ArrayType) String 

```go
func (t *ArrayType) String() string
```

type Attr 
---------

An Attr identifies the attribute type in a DWARF Entry\'s Field.

```go
type Attr uint32
```

```go
const (
    AttrSibling        Attr = 0x01
    AttrLocation       Attr = 0x02
    AttrName           Attr = 0x03
    AttrOrdering       Attr = 0x09
    AttrByteSize       Attr = 0x0B
    AttrBitOffset      Attr = 0x0C
    AttrBitSize        Attr = 0x0D
    AttrStmtList       Attr = 0x10
    AttrLowpc          Attr = 0x11
    AttrHighpc         Attr = 0x12
    AttrLanguage       Attr = 0x13
    AttrDiscr          Attr = 0x15
    AttrDiscrValue     Attr = 0x16
    AttrVisibility     Attr = 0x17
    AttrImport         Attr = 0x18
    AttrStringLength   Attr = 0x19
    AttrCommonRef      Attr = 0x1A
    AttrCompDir        Attr = 0x1B
    AttrConstValue     Attr = 0x1C
    AttrContainingType Attr = 0x1D
    AttrDefaultValue   Attr = 0x1E
    AttrInline         Attr = 0x20
    AttrIsOptional     Attr = 0x21
    AttrLowerBound     Attr = 0x22
    AttrProducer       Attr = 0x25
    AttrPrototyped     Attr = 0x27
    AttrReturnAddr     Attr = 0x2A
    AttrStartScope     Attr = 0x2C
    AttrStrideSize     Attr = 0x2E
    AttrUpperBound     Attr = 0x2F
    AttrAbstractOrigin Attr = 0x31
    AttrAccessibility  Attr = 0x32
    AttrAddrClass      Attr = 0x33
    AttrArtificial     Attr = 0x34
    AttrBaseTypes      Attr = 0x35
    AttrCalling        Attr = 0x36
    AttrCount          Attr = 0x37
    AttrDataMemberLoc  Attr = 0x38
    AttrDeclColumn     Attr = 0x39
    AttrDeclFile       Attr = 0x3A
    AttrDeclLine       Attr = 0x3B
    AttrDeclaration    Attr = 0x3C
    AttrDiscrList      Attr = 0x3D
    AttrEncoding       Attr = 0x3E
    AttrExternal       Attr = 0x3F
    AttrFrameBase      Attr = 0x40
    AttrFriend         Attr = 0x41
    AttrIdentifierCase Attr = 0x42
    AttrMacroInfo      Attr = 0x43
    AttrNamelistItem   Attr = 0x44
    AttrPriority       Attr = 0x45
    AttrSegment        Attr = 0x46
    AttrSpecification  Attr = 0x47
    AttrStaticLink     Attr = 0x48
    AttrType           Attr = 0x49
    AttrUseLocation    Attr = 0x4A
    AttrVarParam       Attr = 0x4B
    AttrVirtuality     Attr = 0x4C
    AttrVtableElemLoc  Attr = 0x4D
    // The following are new in DWARF 3.
    AttrAllocated     Attr = 0x4E
    AttrAssociated    Attr = 0x4F
    AttrDataLocation  Attr = 0x50
    AttrStride        Attr = 0x51
    AttrEntrypc       Attr = 0x52
    AttrUseUTF8       Attr = 0x53
    AttrExtension     Attr = 0x54
    AttrRanges        Attr = 0x55
    AttrTrampoline    Attr = 0x56
    AttrCallColumn    Attr = 0x57
    AttrCallFile      Attr = 0x58
    AttrCallLine      Attr = 0x59
    AttrDescription   Attr = 0x5A
    AttrBinaryScale   Attr = 0x5B
    AttrDecimalScale  Attr = 0x5C
    AttrSmall         Attr = 0x5D
    AttrDecimalSign   Attr = 0x5E
    AttrDigitCount    Attr = 0x5F
    AttrPictureString Attr = 0x60
    AttrMutable       Attr = 0x61
    AttrThreadsScaled Attr = 0x62
    AttrExplicit      Attr = 0x63
    AttrObjectPointer Attr = 0x64
    AttrEndianity     Attr = 0x65
    AttrElemental     Attr = 0x66
    AttrPure          Attr = 0x67
    AttrRecursive     Attr = 0x68
    // The following are new in DWARF 4.
    AttrSignature      Attr = 0x69
    AttrMainSubprogram Attr = 0x6A
    AttrDataBitOffset  Attr = 0x6B
    AttrConstExpr      Attr = 0x6C
    AttrEnumClass      Attr = 0x6D
    AttrLinkageName    Attr = 0x6E
    // The following are new in DWARF 5.
    AttrStringLengthBitSize  Attr = 0x6F
    AttrStringLengthByteSize Attr = 0x70
    AttrRank                 Attr = 0x71
    AttrStrOffsetsBase       Attr = 0x72
    AttrAddrBase             Attr = 0x73
    AttrRnglistsBase         Attr = 0x74
    AttrDwoName              Attr = 0x76
    AttrReference            Attr = 0x77
    AttrRvalueReference      Attr = 0x78
    AttrMacros               Attr = 0x79
    AttrCallAllCalls         Attr = 0x7A
    AttrCallAllSourceCalls   Attr = 0x7B
    AttrCallAllTailCalls     Attr = 0x7C
    AttrCallReturnPC         Attr = 0x7D
    AttrCallValue            Attr = 0x7E
    AttrCallOrigin           Attr = 0x7F
    AttrCallParameter        Attr = 0x80
    AttrCallPC               Attr = 0x81
    AttrCallTailCall         Attr = 0x82
    AttrCallTarget           Attr = 0x83
    AttrCallTargetClobbered  Attr = 0x84
    AttrCallDataLocation     Attr = 0x85
    AttrCallDataValue        Attr = 0x86
    AttrNoreturn             Attr = 0x87
    AttrAlignment            Attr = 0x88
    AttrExportSymbols        Attr = 0x89
    AttrDeleted              Attr = 0x8A
    AttrDefaulted            Attr = 0x8B
    AttrLoclistsBase         Attr = 0x8C
)
```

### func (Attr) GoString 

```go
func (a Attr) GoString() string
```

### func (Attr) String 

```go
func (i Attr) String() string
```

type BasicType 
--------------

A BasicType holds fields common to all basic types.

See the documentation for StructField for more info on the
interpretation of the BitSize/BitOffset/DataBitOffset fields.

```go
type BasicType struct {
    CommonType
    BitSize       int64
    BitOffset     int64
    DataBitOffset int64 // Go 1.18
}
```

### func (\*BasicType) Basic 

```go
func (b *BasicType) Basic() *BasicType
```

### func (\*BasicType) String 

```go
func (t *BasicType) String() string
```

type BoolType 
-------------

A BoolType represents a boolean type.

```go
type BoolType struct {
    BasicType
}
```

type CharType 
-------------

A CharType represents a signed character type.

```go
type CharType struct {
    BasicType
}
```

type Class 
-----------------------------------------

A Class is the DWARF 4 class of an attribute value.

In general, a given attribute\'s value may take on one of several
possible classes defined by DWARF, each of which leads to a slightly
different interpretation of the attribute.

DWARF version 4 distinguishes attribute value classes more finely than
previous versions of DWARF. The reader will disambiguate coarser classes
from earlier versions of DWARF into the appropriate DWARF 4 class. For
example, DWARF 2 uses \"constant\" for constants as well as all types of
section offsets, but the reader will canonicalize attributes in DWARF 2
files that refer to section offsets to one of the Class\*Ptr classes,
even though these classes were only defined in DWARF 3.

```go
type Class int
```

```go
const (
    // ClassUnknown represents values of unknown DWARF class.
    ClassUnknown Class = iota

    // ClassAddress represents values of type uint64 that are
    // addresses on the target machine.
    ClassAddress

    // ClassBlock represents values of type []byte whose
    // interpretation depends on the attribute.
    ClassBlock

    // ClassConstant represents values of type int64 that are
    // constants. The interpretation of this constant depends on
    // the attribute.
    ClassConstant

    // ClassExprLoc represents values of type []byte that contain
    // an encoded DWARF expression or location description.
    ClassExprLoc

    // ClassFlag represents values of type bool.
    ClassFlag

    // ClassLinePtr represents values that are an int64 offset
    // into the "line" section.
    ClassLinePtr

    // ClassLocListPtr represents values that are an int64 offset
    // into the "loclist" section.
    ClassLocListPtr

    // ClassMacPtr represents values that are an int64 offset into
    // the "mac" section.
    ClassMacPtr

    // ClassRangeListPtr represents values that are an int64 offset into
    // the "rangelist" section.
    ClassRangeListPtr

    // ClassReference represents values that are an Offset offset
    // of an Entry in the info section (for use with Reader.Seek).
    // The DWARF specification combines ClassReference and
    // ClassReferenceSig into class "reference".
    ClassReference

    // ClassReferenceSig represents values that are a uint64 type
    // signature referencing a type Entry.
    ClassReferenceSig

    // ClassString represents values that are strings. If the
    // compilation unit specifies the AttrUseUTF8 flag (strongly
    // recommended), the string value will be encoded in UTF-8.
    // Otherwise, the encoding is unspecified.
    ClassString

    // ClassReferenceAlt represents values of type int64 that are
    // an offset into the DWARF "info" section of an alternate
    // object file.
    ClassReferenceAlt

    // ClassStringAlt represents values of type int64 that are an
    // offset into the DWARF string section of an alternate object
    // file.
    ClassStringAlt

    // ClassAddrPtr represents values that are an int64 offset
    // into the "addr" section.
    ClassAddrPtr

    // ClassLocList represents values that are an int64 offset
    // into the "loclists" section.
    ClassLocList

    // ClassRngList represents values that are a uint64 offset
    // from the base of the "rnglists" section.
    ClassRngList

    // ClassRngListsPtr represents values that are an int64 offset
    // into the "rnglists" section. These are used as the base for
    // ClassRngList values.
    ClassRngListsPtr

    // ClassStrOffsetsPtr represents values that are an int64
    // offset into the "str_offsets" section.
    ClassStrOffsetsPtr
)
```

### func (Class) GoString 

```go
func (i Class) GoString() string
```

### func (Class) String 

```go
func (i Class) String() string
```

type CommonType 
---------------

A CommonType holds fields common to multiple types. If a field is not
known or not applicable for a given type, the zero value is used.

```go
type CommonType struct {
    ByteSize int64  // size of value of this type, in bytes
    Name     string // name that can be used to refer to type
}
```

### func (\*CommonType) Common 

```go
func (c *CommonType) Common() *CommonType
```

### func (\*CommonType) Size 

```go
func (c *CommonType) Size() int64
```

type ComplexType 
----------------

A ComplexType represents a complex floating point type.

```go
type ComplexType struct {
    BasicType
}
```

type Data 
---------

Data represents the DWARF debugging information loaded from an
executable file (for example, an ELF or Mach-O executable).

```go
type Data struct {
    // contains filtered or unexported fields
}
```

### func New 

```go
func New(abbrev, aranges, frame, info, line, pubnames, ranges, str []byte) (*Data, error)
```

New returns a new Data object initialized from the given parameters.
Rather than calling this function directly, clients should typically use
the DWARF method of the File type of the appropriate package debug/elf,
debug/macho, or debug/pe.

The \[\]byte arguments are the data from the corresponding debug section
in the object file; for example, for an ELF object, abbrev is the
contents of the \".debug\_abbrev\" section.

### func (\*Data) AddSection 

```go
func (d *Data) AddSection(name string, contents []byte) error
```

AddSection adds another DWARF section by name. The name should be a
DWARF section name such as \".debug\_addr\", \".debug\_str\_offsets\",
and so forth. This approach is used for new DWARF sections added in
DWARF 5 and later.

### func (\*Data) AddTypes 

```go
func (d *Data) AddTypes(name string, types []byte) error
```

AddTypes will add one .debug\_types section to the DWARF data. A typical
object with DWARF version 4 debug info will have multiple .debug\_types
sections. The name is used for error reporting only, and serves to
distinguish one .debug\_types section from another.

### func (\*Data) LineReader 

```go
func (d *Data) LineReader(cu *Entry) (*LineReader, error)
```

LineReader returns a new reader for the line table of compilation unit
cu, which must be an Entry with tag TagCompileUnit.

If this compilation unit has no line table, it returns nil, nil.

### func (\*Data) Ranges 

```go
func (d *Data) Ranges(e *Entry) ([][2]uint64, error)
```

Ranges returns the PC ranges covered by e, a slice of \[low,high) pairs.
Only some entry types, such as TagCompileUnit or TagSubprogram, have PC
ranges; for others, this will return nil with no error.

### func (\*Data) Reader 

```go
func (d *Data) Reader() *Reader
```

Reader returns a new Reader for Data. The reader is positioned at byte
offset 0 in the DWARF "info" section.

### func (\*Data) Type 

```go
func (d *Data) Type(off Offset) (Type, error)
```

Type reads the type at off in the DWARF "info" section.

type DecodeError 
----------------

```go
type DecodeError struct {
    Name   string
    Offset Offset
    Err    string
}
```

### func (DecodeError) Error 

```go
func (e DecodeError) Error() string
```

type DotDotDotType 
------------------

A DotDotDotType represents the variadic \... function parameter.

```go
type DotDotDotType struct {
    CommonType
}
```

### func (\*DotDotDotType) String 

```go
func (t *DotDotDotType) String() string
```

type Entry 
----------

An entry is a sequence of attribute/value pairs.

```go
type Entry struct {
    Offset   Offset // offset of Entry in DWARF info
    Tag      Tag    // tag (kind of Entry)
    Children bool   // whether Entry is followed by children
    Field    []Field
}
```

### func (\*Entry) AttrField 

```go
func (e *Entry) AttrField(a Attr) *Field
```

AttrField returns the Field associated with attribute Attr in Entry, or
nil if there is no such attribute.

### func (\*Entry) Val 

```go
func (e *Entry) Val(a Attr) any
```

Val returns the value associated with attribute Attr in Entry, or nil if
there is no such attribute.

A common idiom is to merge the check for nil return with the check that
the value has the expected dynamic type, as in:

```go
v, ok := e.Val(AttrSibling).(int64)
```

type EnumType 
-------------

An EnumType represents an enumerated type. The only indication of its
native integer type is its ByteSize (inside CommonType).

```go
type EnumType struct {
    CommonType
    EnumName string
    Val      []*EnumValue
}
```

### func (\*EnumType) String 

```go
func (t *EnumType) String() string
```

type EnumValue 
--------------

An EnumValue represents a single enumeration value.

```go
type EnumValue struct {
    Name string
    Val  int64
}
```

type Field 
----------

A Field is a single attribute/value pair in an Entry.

A value can be one of several \"attribute classes\" defined by DWARF.
The Go types corresponding to each class are:

```go
DWARF class       Go type        Class
-----------       -------        -----
address           uint64         ClassAddress
block             []byte         ClassBlock
constant          int64          ClassConstant
flag              bool           ClassFlag
reference
  to info         dwarf.Offset   ClassReference
  to type unit    uint64         ClassReferenceSig
string            string         ClassString
exprloc           []byte         ClassExprLoc
lineptr           int64          ClassLinePtr
loclistptr        int64          ClassLocListPtr
macptr            int64          ClassMacPtr
rangelistptr      int64          ClassRangeListPtr
```

For unrecognized or vendor-defined attributes, Class may be
ClassUnknown.

```go
type Field struct {
    Attr  Attr
    Val   any
    Class Class // Go 1.5
}
```

type FloatType 
--------------

A FloatType represents a floating point type.

```go
type FloatType struct {
    BasicType
}
```

type FuncType 
-------------

A FuncType represents a function type.

```go
type FuncType struct {
    CommonType
    ReturnType Type
    ParamType  []Type
}
```

### func (\*FuncType) String 

```go
func (t *FuncType) String() string
```

type IntType 
------------

An IntType represents a signed integer type.

```go
type IntType struct {
    BasicType
}
```

type LineEntry 
---------------------------------------------

A LineEntry is a row in a DWARF line table.

```go
type LineEntry struct {
    // Address is the program-counter value of a machine
    // instruction generated by the compiler. This LineEntry
    // applies to each instruction from Address to just before the
    // Address of the next LineEntry.
    Address uint64

    // OpIndex is the index of an operation within a VLIW
    // instruction. The index of the first operation is 0. For
    // non-VLIW architectures, it will always be 0. Address and
    // OpIndex together form an operation pointer that can
    // reference any individual operation within the instruction
    // stream.
    OpIndex int

    // File is the source file corresponding to these
    // instructions.
    File *LineFile

    // Line is the source code line number corresponding to these
    // instructions. Lines are numbered beginning at 1. It may be
    // 0 if these instructions cannot be attributed to any source
    // line.
    Line int

    // Column is the column number within the source line of these
    // instructions. Columns are numbered beginning at 1. It may
    // be 0 to indicate the "left edge" of the line.
    Column int

    // IsStmt indicates that Address is a recommended breakpoint
    // location, such as the beginning of a line, statement, or a
    // distinct subpart of a statement.
    IsStmt bool

    // BasicBlock indicates that Address is the beginning of a
    // basic block.
    BasicBlock bool

    // PrologueEnd indicates that Address is one (of possibly
    // many) PCs where execution should be suspended for a
    // breakpoint on entry to the containing function.
    //
    // Added in DWARF 3.
    PrologueEnd bool

    // EpilogueBegin indicates that Address is one (of possibly
    // many) PCs where execution should be suspended for a
    // breakpoint on exit from this function.
    //
    // Added in DWARF 3.
    EpilogueBegin bool

    // ISA is the instruction set architecture for these
    // instructions. Possible ISA values should be defined by the
    // applicable ABI specification.
    //
    // Added in DWARF 3.
    ISA int

    // Discriminator is an arbitrary integer indicating the block
    // to which these instructions belong. It serves to
    // distinguish among multiple blocks that may all have with
    // the same source file, line, and column. Where only one
    // block exists for a given source position, it should be 0.
    //
    // Added in DWARF 3.
    Discriminator int

    // EndSequence indicates that Address is the first byte after
    // the end of a sequence of target machine instructions. If it
    // is set, only this and the Address field are meaningful. A
    // line number table may contain information for multiple
    // potentially disjoint instruction sequences. The last entry
    // in a line table should always have EndSequence set.
    EndSequence bool
}
```

type LineFile 
--------------------------------------------

A LineFile is a source file referenced by a DWARF line table entry.

```go
type LineFile struct {
    Name   string
    Mtime  uint64 // Implementation defined modification time, or 0 if unknown
    Length int    // File length, or 0 if unknown
}
```

type LineReader 
----------------------------------------------

A LineReader reads a sequence of LineEntry structures from a DWARF
\"line\" section for a single compilation unit. LineEntries occur in
order of increasing PC and each LineEntry gives metadata for the
instructions from that LineEntry\'s PC to just before the next
LineEntry\'s PC. The last entry will have its EndSequence field set.

```go
type LineReader struct {
    // contains filtered or unexported fields
}
```

### func (\*LineReader) Files 

```go
func (r *LineReader) Files() []*LineFile
```

Files returns the file name table of this compilation unit as of the
current position in the line table. The file name table may be
referenced from attributes in this compilation unit such as
AttrDeclFile.

Entry 0 is always nil, since file index 0 represents \"no file\".

The file name table of a compilation unit is not fixed. Files returns
the file table as of the current position in the line table. This may
contain more entries than the file table at an earlier position in the
line table, though existing entries never change.

### func (\*LineReader) Next 

```go
func (r *LineReader) Next(entry *LineEntry) error
```

Next sets \*entry to the next row in this line table and moves to the
next row. If there are no more entries and the line table is properly
terminated, it returns io.EOF.

Rows are always in order of increasing entry.Address, but entry.Line may
go forward or backward.

### func (\*LineReader) Reset 

```go
func (r *LineReader) Reset()
```

Reset repositions the line table reader at the beginning of the line
table.

### func (\*LineReader) Seek 

```go
func (r *LineReader) Seek(pos LineReaderPos)
```

Seek restores the line table reader to a position returned by Tell.

The argument pos must have been returned by a call to Tell on this line
table.

### func (\*LineReader) SeekPC 

```go
func (r *LineReader) SeekPC(pc uint64, entry *LineEntry) error
```

SeekPC sets \*entry to the LineEntry that includes pc and positions the
reader on the next entry in the line table. If necessary, this will seek
backwards to find pc.

If pc is not covered by any entry in this line table, SeekPC returns
ErrUnknownPC. In this case, \*entry and the final seek position are
unspecified.

Note that DWARF line tables only permit sequential, forward scans.
Hence, in the worst case, this takes time linear in the size of the line
table. If the caller wishes to do repeated fast PC lookups, it should
build an appropriate index of the line table.

### func (\*LineReader) Tell 

```go
func (r *LineReader) Tell() LineReaderPos
```

Tell returns the current position in the line table.

type LineReaderPos 
-------------------------------------------------

A LineReaderPos represents a position in a line table.

```go
type LineReaderPos struct {
    // contains filtered or unexported fields
}
```

type Offset 
-----------

An Offset represents the location of an Entry within the DWARF info.
(See Reader.Seek.)

```go
type Offset uint32
```

type PtrType 
------------

A PtrType represents a pointer type.

```go
type PtrType struct {
    CommonType
    Type Type
}
```

### func (\*PtrType) String 

```go
func (t *PtrType) String() string
```

type QualType 
-------------

A QualType represents a type that has the C/C++ \"const\", \"restrict\",
or \"volatile\" qualifier.

```go
type QualType struct {
    CommonType
    Qual string
    Type Type
}
```

### func (\*QualType) Size 

```go
func (t *QualType) Size() int64
```

### func (\*QualType) String 

```go
func (t *QualType) String() string
```

type Reader 
-----------

A Reader allows reading Entry structures from a DWARF "info" section.
The Entry structures are arranged in a tree. The Reader\'s Next function
return successive entries from a pre-order traversal of the tree. If an
entry has children, its Children field will be true, and the children
follow, terminated by an Entry with Tag 0.

```go
type Reader struct {
    // contains filtered or unexported fields
}
```

### func (\*Reader) AddressSize 

```go
func (r *Reader) AddressSize() int
```

AddressSize returns the size in bytes of addresses in the current
compilation unit.

### func (\*Reader) ByteOrder 

```go
func (r *Reader) ByteOrder() binary.ByteOrder
```

ByteOrder returns the byte order in the current compilation unit.

### func (\*Reader) Next 

```go
func (r *Reader) Next() (*Entry, error)
```

Next reads the next entry from the encoded entry stream. It returns nil,
nil when it reaches the end of the section. It returns an error if the
current offset is invalid or the data at the offset cannot be decoded as
a valid Entry.

### func (\*Reader) Seek 

```go
func (r *Reader) Seek(off Offset)
```

Seek positions the Reader at offset off in the encoded entry stream.
Offset 0 can be used to denote the first entry.

### func (\*Reader) SeekPC 

```go
func (r *Reader) SeekPC(pc uint64) (*Entry, error)
```

SeekPC returns the Entry for the compilation unit that includes pc, and
positions the reader to read the children of that unit. If pc is not
covered by any unit, SeekPC returns ErrUnknownPC and the position of the
reader is undefined.

Because compilation units can describe multiple regions of the
executable, in the worst case SeekPC must search through all the ranges
in all the compilation units. Each call to SeekPC starts the search at
the compilation unit of the last call, so in general looking up a series
of PCs will be faster if they are sorted. If the caller wishes to do
repeated fast PC lookups, it should build an appropriate index using the
Ranges method.

### func (\*Reader) SkipChildren 

```go
func (r *Reader) SkipChildren()
```

SkipChildren skips over the child entries associated with the last Entry
returned by Next. If that Entry did not have children or Next has not
been called, SkipChildren is a no-op.

type StructField 
----------------

A StructField represents a field in a struct, union, or C++ class type.

### Bit Fields 

The BitSize, BitOffset, and DataBitOffset fields describe the bit size
and offset of data members declared as bit fields in C/C++
struct/union/class types.

BitSize is the number of bits in the bit field.

DataBitOffset, if non-zero, is the number of bits from the start of the
enclosing entity (e.g. containing struct/class/union) to the start of
the bit field. This corresponds to the DW\_AT\_data\_bit\_offset DWARF
attribute that was introduced in DWARF 4.

BitOffset, if non-zero, is the number of bits between the most
significant bit of the storage unit holding the bit field to the most
significant bit of the bit field. Here \"storage unit\" is the type name
before the bit field (for a field \"unsigned x:17\", the storage unit is
\"unsigned\"). BitOffset values can vary depending on the endianness of
the system. BitOffset corresponds to the DW\_AT\_bit\_offset DWARF
attribute that was deprecated in DWARF 4 and removed in DWARF 5.

At most one of DataBitOffset and BitOffset will be non-zero;
DataBitOffset/BitOffset will only be non-zero if BitSize is non-zero.
Whether a C compiler uses one or the other will depend on compiler
vintage and command line options.

Here is an example of C/C++ bit field use, along with what to expect in
terms of DWARF bit offset info. Consider this code:

```go
struct S {
    int q;
    int j:5;
    int k:6;
    int m:5;
    int n:8;
} s;
```

For the code above, one would expect to see the following for
DW\_AT\_bit\_offset values (using GCC 8):

```go
       Little   |     Big
       Endian   |    Endian
                |
"j":     27     |     0
"k":     21     |     5
"m":     16     |     11
"n":     8      |     16
```

Note that in the above the offsets are purely with respect to the
containing storage unit for j/k/m/n \-- these values won\'t vary based
on the size of prior data members in the containing struct.

If the compiler emits DW\_AT\_data\_bit\_offset, the expected values
would be:

```go
"j":     32
"k":     37
"m":     43
"n":     48
```

Here the value 32 for \"j\" reflects the fact that the bit field is
preceded by other data members (recall that DW\_AT\_data\_bit\_offset
values are relative to the start of the containing struct). Hence
DW\_AT\_data\_bit\_offset values can be quite large for structs with
many fields.

DWARF also allow for the possibility of base types that have non-zero
bit size and bit offset, so this information is also captured for base
types, but it is worth noting that it is not possible to trigger this
behavior using mainstream languages.

```go
type StructField struct {
    Name          string
    Type          Type
    ByteOffset    int64
    ByteSize      int64 // usually zero; use Type.Size() for normal fields
    BitOffset     int64
    DataBitOffset int64 // Go 1.18
    BitSize       int64 // zero if not a bit field
}
```

type StructType 
---------------

A StructType represents a struct, union, or C++ class type.

```go
type StructType struct {
    CommonType
    StructName string
    Kind       string // "struct", "union", or "class".
    Field      []*StructField
    Incomplete bool // if true, struct, union, class is declared but not defined
}
```

### func (\*StructType) Defn 

```go
func (t *StructType) Defn() string
```

### func (\*StructType) String 

```go
func (t *StructType) String() string
```

type Tag 
--------

A Tag is the classification (the type) of an Entry.

```go
type Tag uint32
```

```go
const (
    TagArrayType              Tag = 0x01
    TagClassType              Tag = 0x02
    TagEntryPoint             Tag = 0x03
    TagEnumerationType        Tag = 0x04
    TagFormalParameter        Tag = 0x05
    TagImportedDeclaration    Tag = 0x08
    TagLabel                  Tag = 0x0A
    TagLexDwarfBlock          Tag = 0x0B
    TagMember                 Tag = 0x0D
    TagPointerType            Tag = 0x0F
    TagReferenceType          Tag = 0x10
    TagCompileUnit            Tag = 0x11
    TagStringType             Tag = 0x12
    TagStructType             Tag = 0x13
    TagSubroutineType         Tag = 0x15
    TagTypedef                Tag = 0x16
    TagUnionType              Tag = 0x17
    TagUnspecifiedParameters  Tag = 0x18
    TagVariant                Tag = 0x19
    TagCommonDwarfBlock       Tag = 0x1A
    TagCommonInclusion        Tag = 0x1B
    TagInheritance            Tag = 0x1C
    TagInlinedSubroutine      Tag = 0x1D
    TagModule                 Tag = 0x1E
    TagPtrToMemberType        Tag = 0x1F
    TagSetType                Tag = 0x20
    TagSubrangeType           Tag = 0x21
    TagWithStmt               Tag = 0x22
    TagAccessDeclaration      Tag = 0x23
    TagBaseType               Tag = 0x24
    TagCatchDwarfBlock        Tag = 0x25
    TagConstType              Tag = 0x26
    TagConstant               Tag = 0x27
    TagEnumerator             Tag = 0x28
    TagFileType               Tag = 0x29
    TagFriend                 Tag = 0x2A
    TagNamelist               Tag = 0x2B
    TagNamelistItem           Tag = 0x2C
    TagPackedType             Tag = 0x2D
    TagSubprogram             Tag = 0x2E
    TagTemplateTypeParameter  Tag = 0x2F
    TagTemplateValueParameter Tag = 0x30
    TagThrownType             Tag = 0x31
    TagTryDwarfBlock          Tag = 0x32
    TagVariantPart            Tag = 0x33
    TagVariable               Tag = 0x34
    TagVolatileType           Tag = 0x35
    // The following are new in DWARF 3.
    TagDwarfProcedure  Tag = 0x36
    TagRestrictType    Tag = 0x37
    TagInterfaceType   Tag = 0x38
    TagNamespace       Tag = 0x39
    TagImportedModule  Tag = 0x3A
    TagUnspecifiedType Tag = 0x3B
    TagPartialUnit     Tag = 0x3C
    TagImportedUnit    Tag = 0x3D
    TagMutableType     Tag = 0x3E // Later removed from DWARF.
    TagCondition       Tag = 0x3F
    TagSharedType      Tag = 0x40
    // The following are new in DWARF 4.
    TagTypeUnit            Tag = 0x41
    TagRvalueReferenceType Tag = 0x42
    TagTemplateAlias       Tag = 0x43
    // The following are new in DWARF 5.
    TagCoarrayType       Tag = 0x44
    TagGenericSubrange   Tag = 0x45
    TagDynamicType       Tag = 0x46
    TagAtomicType        Tag = 0x47
    TagCallSite          Tag = 0x48
    TagCallSiteParameter Tag = 0x49
    TagSkeletonUnit      Tag = 0x4A
    TagImmutableType     Tag = 0x4B
)
```

### func (Tag) GoString 

```go
func (t Tag) GoString() string
```

### func (Tag) String 

```go
func (i Tag) String() string
```

type Type 
---------

A Type conventionally represents a pointer to any of the specific Type
structures (CharType, StructType, etc.).

```go
type Type interface {
    Common() *CommonType
    String() string
    Size() int64
}
```

type TypedefType 
----------------

A TypedefType represents a named type.

```go
type TypedefType struct {
    CommonType
    Type Type
}
```

### func (\*TypedefType) Size 

```go
func (t *TypedefType) Size() int64
```

### func (\*TypedefType) String 

```go
func (t *TypedefType) String() string
```

type UcharType 
--------------

A UcharType represents an unsigned character type.

```go
type UcharType struct {
    BasicType
}
```

type UintType 
-------------

A UintType represents an unsigned integer type.

```go
type UintType struct {
    BasicType
}
```

type UnspecifiedType 
---------------------------------------------------

An UnspecifiedType represents an implicit, unknown, ambiguous or
nonexistent type.

```go
type UnspecifiedType struct {
    BasicType
}
```

type UnsupportedType 
-----------------------------------------------------

An UnsupportedType is a placeholder returned in situations where we
encounter a type that isn\'t supported.

```go
type UnsupportedType struct {
    CommonType
    Tag Tag
}
```

### func (\*UnsupportedType) String 

```go
func (t *UnsupportedType) String() string
```

type VoidType 
-------------

A VoidType represents the C void type.

```go
type VoidType struct {
    CommonType
}
```

### func (\*VoidType) String 

```go
func (t *VoidType) String() string
```

 
© Google, Inc.\
Licensed under the Creative Commons Attribution License 3.0.\
https://golang.org/pkg/debug/dwarf/>


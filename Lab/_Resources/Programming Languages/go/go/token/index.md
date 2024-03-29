Package token
=============

-   `import "go/token"`
-   [Overview](#pkg-overview)
-   [Index](#pkg-index)
-   [Examples](#pkg-examples)

Overview 
--------

Package token defines constants representing the lexical tokens of the
Go programming language and basic operations on tokens (printing,
predicates).

#### [Example (RetrievePositionInfo)]

Code:

```go
fset := token.NewFileSet()

const src = `package main

import "fmt"

import "go/token"


type p = token.Pos

const bad = token.NoPos


func ok(pos p) bool {
    return pos != bad
}

/*line :7:9*/func main() {
    fmt.Println(ok(bad) == bad.IsValid())
}
`

f, err := parser.ParseFile(fset, "main.go", src, 0)
if err != nil {
    fmt.Println(err)
    return
}

// Print the location and kind of each declaration in f.
for _, decl := range f.Decls {
    // Get the filename, line, and column back via the file set.
    // We get both the relative and absolute position.
    // The relative position is relative to the last line directive.
    // The absolute position is the exact position in the source.
    pos := decl.Pos()
    relPosition := fset.Position(pos)
    absPosition := fset.PositionFor(pos, false)

    // Either a FuncDecl or GenDecl, since we exit on error.
    kind := "func"
    if gen, ok := decl.(*ast.GenDecl); ok {
        kind = gen.Tok.String()
    }

    // If the relative and absolute positions differ, show both.
    fmtPosition := relPosition.String()
    if relPosition != absPosition {
        fmtPosition += "[" + absPosition.String() + "]"
    }

    fmt.Printf("%s: %s\n", fmtPosition, kind)
}
```

Output:

```go
main.go:3:1: import
main.go:5:1: import
main.go:1:5[main.go:8:1]: type
main.go:3:1[main.go:10:1]: const
fake.go:42:11[main.go:13:1]: func
fake.go:7:9[main.go:17:14]: func
```

Index 
-----

-   [Constants](#pkg-constants)
-   [func IsExported(name string) bool](#IsExported)
-   [func IsIdentifier(name string) bool](#IsIdentifier)
-   [func IsKeyword(name string) bool](#IsKeyword)
-   [type File](#File)
-   [func (f \*File) AddLine(offset int)](#File.AddLine)
-   [func (f \*File) AddLineColumnInfo(offset int, filename string,
    line, column int)](#File.AddLineColumnInfo)
-   [func (f \*File) AddLineInfo(offset int, filename string, line
    int)](#File.AddLineInfo)
-   [func (f \*File) Base() int](#File.Base)
-   [func (f \*File) Line(p Pos) int](#File.Line)
-   [func (f \*File) LineCount() int](#File.LineCount)
-   [func (f \*File) LineStart(line int) Pos](#File.LineStart)
-   [func (f \*File) Lines() \[\]int](#File.Lines)
-   [func (f \*File) MergeLine(line int)](#File.MergeLine)
-   [func (f \*File) Name() string](#File.Name)
-   [func (f \*File) Offset(p Pos) int](#File.Offset)
-   [func (f \*File) Pos(offset int) Pos](#File.Pos)
-   [func (f \*File) Position(p Pos) (pos Position)](#File.Position)
-   [func (f \*File) PositionFor(p Pos, adjusted bool) (pos
    Position)](#File.PositionFor)
-   [func (f \*File) SetLines(lines \[\]int) bool](#File.SetLines)
-   [func (f \*File) SetLinesForContent(content
    \[\]byte)](#File.SetLinesForContent)
-   [func (f \*File) Size() int](#File.Size)
-   [type FileSet](#FileSet)
-   [func NewFileSet() \*FileSet](#NewFileSet)
-   [func (s \*FileSet) AddFile(filename string, base, size int)
    \*File](#FileSet.AddFile)
-   [func (s \*FileSet) Base() int](#FileSet.Base)
-   [func (s \*FileSet) File(p Pos) (f \*File)](#FileSet.File)
-   [func (s \*FileSet) Iterate(f func(\*File) bool)](#FileSet.Iterate)
-   [func (s \*FileSet) Position(p Pos) (pos
    Position)](#FileSet.Position)
-   [func (s \*FileSet) PositionFor(p Pos, adjusted bool) (pos
    Position)](#FileSet.PositionFor)
-   [func (s \*FileSet) Read(decode func(any) error)
    error](#FileSet.Read)
-   [func (s \*FileSet) RemoveFile(file \*File)](#FileSet.RemoveFile)
-   [func (s \*FileSet) Write(encode func(any) error)
    error](#FileSet.Write)
-   [type Pos](#Pos)
-   [func (p Pos) IsValid() bool](#Pos.IsValid)
-   [type Position](#Position)
-   [func (pos \*Position) IsValid() bool](#Position.IsValid)
-   [func (pos Position) String() string](#Position.String)
-   [type Token](#Token)
-   [func Lookup(ident string) Token](#Lookup)
-   [func (tok Token) IsKeyword() bool](#Token.IsKeyword)
-   [func (tok Token) IsLiteral() bool](#Token.IsLiteral)
-   [func (tok Token) IsOperator() bool](#Token.IsOperator)
-   [func (op Token) Precedence() int](#Token.Precedence)
-   [func (tok Token) String() string](#Token.String)

 
### Examples

[Package
(RetrievePositionInfo)](#example__retrievePositionInfo)


### Package files

position.go serialize.go token.go

Constants 
---------

A set of constants for precedence-based expression parsing.
Non-operators have lowest precedence, followed by operators starting
with precedence 1 up to unary operators. The highest precedence serves
as \"catch-all\" precedence for selector, indexing, and other operator
and delimiter tokens.

```go
const (
    LowestPrec  = 0 // non-operators
    UnaryPrec   = 6
    HighestPrec = 7
)
```

func IsExported 
------------------------------------------------

```go
func IsExported(name string) bool
```

IsExported reports whether name starts with an upper-case letter.

func IsIdentifier 
--------------------------------------------------

```go
func IsIdentifier(name string) bool
```

IsIdentifier reports whether name is a Go identifier, that is, a
non-empty string made up of letters, digits, and underscores, where the
first character is not a digit. Keywords are not identifiers.

func IsKeyword 
-----------------------------------------------

```go
func IsKeyword(name string) bool
```

IsKeyword reports whether name is a Go keyword, such as \"func\" or
\"return\".

type File 
---------

A File is a handle for a file belonging to a FileSet. A File has a name,
size, and line offset table.

```go
type File struct {
    // contains filtered or unexported fields
}
```

### func (\*File) AddLine 

```go
func (f *File) AddLine(offset int)
```

AddLine adds the line offset for a new line. The line offset must be
larger than the offset for the previous line and smaller than the file
size; otherwise the line offset is ignored.

### func (\*File) AddLineColumnInfo 

```go
func (f *File) AddLineColumnInfo(offset int, filename string, line, column int)
```

AddLineColumnInfo adds alternative file, line, and column number
information for a given file offset. The offset must be larger than the
offset for the previously added alternative line info and smaller than
the file size; otherwise the information is ignored.

AddLineColumnInfo is typically used to register alternative position
information for line directives such as //line filename:line:column.

### func (\*File) AddLineInfo 

```go
func (f *File) AddLineInfo(offset int, filename string, line int)
```

AddLineInfo is like AddLineColumnInfo with a column = 1 argument. It is
here for backward-compatibility for code prior to Go 1.11.

### func (\*File) Base 

```go
func (f *File) Base() int
```

Base returns the base offset of file f as registered with AddFile.

### func (\*File) Line 

```go
func (f *File) Line(p Pos) int
```

Line returns the line number for the given file position p; p must be a
Pos value in that file or NoPos.

### func (\*File) LineCount 

```go
func (f *File) LineCount() int
```

LineCount returns the number of lines in file f.

### func (\*File) LineStart 

```go
func (f *File) LineStart(line int) Pos
```

LineStart returns the Pos value of the start of the specified line. It
ignores any alternative positions set using AddLineColumnInfo. LineStart
panics if the 1-based line number is invalid.

### func (\*File) Lines 

```go
func (f *File) Lines() []int
```

Lines returns the effective line offset table of the form described by
SetLines. Callers must not mutate the result.

### func (\*File) MergeLine 

```go
func (f *File) MergeLine(line int)
```

MergeLine merges a line with the following line. It is akin to replacing
the newline character at the end of the line with a space (to not change
the remaining offsets). To obtain the line number, consult e.g.
Position.Line. MergeLine will panic if given an invalid line number.

### func (\*File) Name 

```go
func (f *File) Name() string
```

Name returns the file name of file f as registered with AddFile.

### func (\*File) Offset 

```go
func (f *File) Offset(p Pos) int
```

Offset returns the offset for the given file position p; p must be a
valid Pos value in that file. f.Offset(f.Pos(offset)) == offset.

### func (\*File) Pos 

```go
func (f *File) Pos(offset int) Pos
```

Pos returns the Pos value for the given file offset; the offset must be
\<= f.Size(). f.Pos(f.Offset(p)) == p.

### func (\*File) Position 

```go
func (f *File) Position(p Pos) (pos Position)
```

Position returns the Position value for the given file position p.
Calling f.Position(p) is equivalent to calling f.PositionFor(p, true).

### func (\*File) PositionFor 

```go
func (f *File) PositionFor(p Pos, adjusted bool) (pos Position)
```

PositionFor returns the Position value for the given file position p. If
adjusted is set, the position may be adjusted by position-altering
//line comments; otherwise those comments are ignored. p must be a Pos
value in f or NoPos.

### func (\*File) SetLines 

```go
func (f *File) SetLines(lines []int) bool
```

SetLines sets the line offsets for a file and reports whether it
succeeded. The line offsets are the offsets of the first character of
each line; for instance for the content \"ab\\nc\\n\" the line offsets
are {0, 3}. An empty file has an empty line offset table. Each line
offset must be larger than the offset for the previous line and smaller
than the file size; otherwise SetLines fails and returns false. Callers
must not mutate the provided slice after SetLines returns.

### func (\*File) SetLinesForContent 

```go
func (f *File) SetLinesForContent(content []byte)
```

SetLinesForContent sets the line offsets for the given file content. It
ignores position-altering //line comments.

### func (\*File) Size 

```go
func (f *File) Size() int
```

Size returns the size of file f as registered with AddFile.

type FileSet 
------------

A FileSet represents a set of source files. Methods of file sets are
synchronized; multiple goroutines may invoke them concurrently.

The byte offsets for each file in a file set are mapped into distinct
(integer) intervals, one interval \[base, base+size\] per file. Base
represents the first byte in the file, and size is the corresponding
file size. A Pos value is a value in such an interval. By determining
the interval a Pos value belongs to, the file, its file base, and thus
the byte offset (position) the Pos value is representing can be
computed.

When adding a new file, a file base must be provided. That can be any
integer value that is past the end of any interval of any file already
in the file set. For convenience, FileSet.Base provides such a value,
which is simply the end of the Pos interval of the most recently added
file, plus one. Unless there is a need to extend an interval later,
using the FileSet.Base should be used as argument for FileSet.AddFile.

A File may be removed from a FileSet when it is no longer needed. This
may reduce memory usage in a long-running application.

```go
type FileSet struct {
    // contains filtered or unexported fields
}
```

### func NewFileSet 

```go
func NewFileSet() *FileSet
```

NewFileSet creates a new file set.

### func (\*FileSet) AddFile 

```go
func (s *FileSet) AddFile(filename string, base, size int) *File
```

AddFile adds a new file with a given filename, base offset, and file
size to the file set s and returns the file. Multiple files may have the
same name. The base offset must not be smaller than the FileSet\'s
Base(), and size must not be negative. As a special case, if a negative
base is provided, the current value of the FileSet\'s Base() is used
instead.

Adding the file will set the file set\'s Base() value to base + size + 1
as the minimum base value for the next file. The following relationship
exists between a Pos value p for a given file offset offs:

```go
int(p) = base + offs
```

with offs in the range \[0, size\] and thus p in the range \[base,
base+size\]. For convenience, File.Pos may be used to create
file-specific position values from a file offset.

### func (\*FileSet) Base 

```go
func (s *FileSet) Base() int
```

Base returns the minimum base offset that must be provided to AddFile
when adding the next file.

### func (\*FileSet) File 

```go
func (s *FileSet) File(p Pos) (f *File)
```

File returns the file that contains the position p. If no such file is
found (for instance for p == NoPos), the result is nil.

### func (\*FileSet) Iterate 

```go
func (s *FileSet) Iterate(f func(*File) bool)
```

Iterate calls f for the files in the file set in the order they were
added until f returns false.

### func (\*FileSet) Position 

```go
func (s *FileSet) Position(p Pos) (pos Position)
```

Position converts a Pos p in the fileset into a Position value. Calling
s.Position(p) is equivalent to calling s.PositionFor(p, true).

### func (\*FileSet) PositionFor 

```go
func (s *FileSet) PositionFor(p Pos, adjusted bool) (pos Position)
```

PositionFor converts a Pos p in the fileset into a Position value. If
adjusted is set, the position may be adjusted by position-altering
//line comments; otherwise those comments are ignored. p must be a Pos
value in s or NoPos.

### func (\*FileSet) Read 

```go
func (s *FileSet) Read(decode func(any) error) error
```

Read calls decode to deserialize a file set into s; s must not be nil.

### func (\*FileSet) RemoveFile 

```go
func (s *FileSet) RemoveFile(file *File)
```

RemoveFile removes a file from the FileSet so that subsequent queries
for its Pos interval yield a negative result. This reduces the memory
usage of a long-lived FileSet that encounters an unbounded stream of
files.

Removing a file that does not belong to the set has no effect.

### func (\*FileSet) Write 

```go
func (s *FileSet) Write(encode func(any) error) error
```

Write calls encode to serialize the file set s.

type Pos 
--------

Pos is a compact encoding of a source position within a file set. It can
be converted into a Position for a more convenient, but much larger,
representation.

The Pos value for a given file is a number in the range \[base,
base+size\], where base and size are specified when a file is added to
the file set. The difference between a Pos value and the corresponding
file base corresponds to the byte offset of that position (represented
by the Pos value) from the beginning of the file. Thus, the file base
offset is the Pos value representing the first byte in the file.

To create the Pos value for a specific source offset (measured in
bytes), first add the respective file to the current file set using
FileSet.AddFile and then call File.Pos(offset) for that file. Given a
Pos value p for a specific file set fset, the corresponding Position
value is obtained by calling fset.Position(p).

Pos values can be compared directly with the usual comparison operators:
If two Pos values p and q are in the same file, comparing p and q is
equivalent to comparing the respective source file offsets. If p and q
are in different files, p \< q is true if the file implied by p was
added to the respective file set before the file implied by q.

```go
type Pos int
```

The zero value for Pos is NoPos; there is no file and line information
associated with it, and NoPos.IsValid() is false. NoPos is always
smaller than any other Pos value. The corresponding Position value for
NoPos is the zero value for Position.

```go
const NoPos Pos = 0
```

### func (Pos) IsValid 

```go
func (p Pos) IsValid() bool
```

IsValid reports whether the position is valid.

type Position 
-------------

Position describes an arbitrary source position including the file,
line, and column location. A Position is valid if the line number is \>
0.

```go
type Position struct {
    Filename string // filename, if any
    Offset   int    // offset, starting at 0
    Line     int    // line number, starting at 1
    Column   int    // column number, starting at 1 (byte count)
}
```

### func (\*Position) IsValid 

```go
func (pos *Position) IsValid() bool
```

IsValid reports whether the position is valid.

### func (Position) String 

```go
func (pos Position) String() string
```

String returns a string in one of several forms:

```go
file:line:column    valid position with file name
file:line           valid position with file name but no column (column == 0)
line:column         valid position without file name
line                valid position without file name and no column (column == 0)
file                invalid position with file name
-                   invalid position without file name
```

type Token 
----------

Token is the set of lexical tokens of the Go programming language.

```go
type Token int
```

The list of tokens.

```go
const (
    // Special tokens
    ILLEGAL Token = iota
    EOF
    COMMENT

    // Identifiers and basic type literals
    // (these tokens stand for classes of literals)
    IDENT  // main
    INT    // 12345
    FLOAT  // 123.45
    IMAG   // 123.45i
    CHAR   // 'a'
    STRING // "abc"

    // Operators and delimiters
    ADD // +
    SUB // -
    MUL // *
    QUO // /
    REM // %

    AND     // &
    OR      // |
    XOR     // ^
    SHL     // <<
    SHR     // >>
    AND_NOT // &^

    ADD_ASSIGN // +=
    SUB_ASSIGN // -=
    MUL_ASSIGN // *=
    QUO_ASSIGN // /=
    REM_ASSIGN // %=

    AND_ASSIGN     // &=
    OR_ASSIGN      // |=
    XOR_ASSIGN     // ^=
    SHL_ASSIGN     // <<=
    SHR_ASSIGN     // >>=
    AND_NOT_ASSIGN // &^=

    LAND  // &&
    LOR   // ||
    ARROW // <-
    INC   // ++
    DEC   // --

    EQL    // ==
    LSS    // <
    GTR    // >
    ASSIGN // =
    NOT    // !

    NEQ      // !=
    LEQ      // <=
    GEQ      // >=
    DEFINE   // :=
    ELLIPSIS // ...

    LPAREN // (
    LBRACK // [
    LBRACE // {
    COMMA  // ,
    PERIOD // .

    RPAREN    // )
    RBRACK    // ]
    RBRACE    // }
    SEMICOLON // ;
    COLON     // :

    // Keywords
    BREAK
    CASE
    CHAN
    CONST
    CONTINUE

    DEFAULT
    DEFER
    ELSE
    FALLTHROUGH
    FOR

    FUNC
    GO
    GOTO
    IF
    IMPORT

    INTERFACE
    MAP
    PACKAGE
    RANGE
    RETURN

    SELECT
    STRUCT
    SWITCH
    TYPE
    VAR

    // additional tokens, handled in an ad-hoc manner
    TILDE
)
```

### func Lookup 

```go
func Lookup(ident string) Token
```

Lookup maps an identifier to its keyword token or IDENT (if not a
keyword).

### func (Token) IsKeyword 

```go
func (tok Token) IsKeyword() bool
```

IsKeyword returns true for tokens corresponding to keywords; it returns
false otherwise.

### func (Token) IsLiteral 

```go
func (tok Token) IsLiteral() bool
```

IsLiteral returns true for tokens corresponding to identifiers and basic
type literals; it returns false otherwise.

### func (Token) IsOperator 

```go
func (tok Token) IsOperator() bool
```

IsOperator returns true for tokens corresponding to operators and
delimiters; it returns false otherwise.

### func (Token) Precedence 

```go
func (op Token) Precedence() int
```

Precedence returns the operator precedence of the binary operator op. If
op is not a binary operator, the result is LowestPrecedence.

### func (Token) String 

```go
func (tok Token) String() string
```

String returns the string corresponding to the token tok. For operators,
delimiters, and keywords the string is the actual token character
sequence (e.g., for the token ADD, the string is \"+\"). For all other
tokens the string corresponds to the token constant name (e.g. for the
token IDENT, the string is \"IDENT\").

 
© Google, Inc.\
Licensed under the Creative Commons Attribution License 3.0.\
https://golang.org/pkg/go/token/>


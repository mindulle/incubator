Package quick
=============

-   `import "testing/quick"`
-   [Overview](#pkg-overview)
-   [Index](#pkg-index)

Overview 
--------

Package quick implements utility functions to help with black box
testing.

The testing/quick package is frozen and is not accepting new features.

Index 
-----

-   [func Check(f any, config \*Config) error](#Check)
-   [func CheckEqual(f, g any, config \*Config) error](#CheckEqual)
-   [func Value(t reflect.Type, rand \*rand.Rand) (value reflect.Value,
    ok bool)](#Value)
-   [type CheckEqualError](#CheckEqualError)
-   [func (s \*CheckEqualError) Error() string](#CheckEqualError.Error)
-   [type CheckError](#CheckError)
-   [func (s \*CheckError) Error() string](#CheckError.Error)
-   [type Config](#Config)
-   [type Generator](#Generator)
-   [type SetupError](#SetupError)
-   [func (s SetupError) Error() string](#SetupError.Error)

### Package files

quick.go

func Check 
----------

```go
func Check(f any, config *Config) error
```

Check looks for an input to f, any function that returns bool, such that
f returns false. It calls f repeatedly, with arbitrary values for each
argument. If f returns false on a given input, Check returns that input
as a \*CheckError. For example:

```go
func TestOddMultipleOfThree(t *testing.T) {
    f := func(x int) bool {
        y := OddMultipleOfThree(x)
        return y%2 == 1 && y%3 == 0
    }
    if err := quick.Check(f, nil); err != nil {
        t.Error(err)
    }
}
```

func CheckEqual 
---------------

```go
func CheckEqual(f, g any, config *Config) error
```

CheckEqual looks for an input on which f and g return different results.
It calls f and g repeatedly with arbitrary values for each argument. If
f and g return different answers, CheckEqual returns a \*CheckEqualError
describing the input and the outputs.

func Value 
----------

```go
func Value(t reflect.Type, rand *rand.Rand) (value reflect.Value, ok bool)
```

Value returns an arbitrary value of the given type. If the type
implements the Generator interface, that will be used. Note: To create
arbitrary values for structs, all the fields must be exported.

type CheckEqualError 
--------------------

A CheckEqualError is the result CheckEqual finding an error.

```go
type CheckEqualError struct {
    CheckError
    Out1 []any
    Out2 []any
}
```

### func (\*CheckEqualError) Error 

```go
func (s *CheckEqualError) Error() string
```

type CheckError 
---------------

A CheckError is the result of Check finding an error.

```go
type CheckError struct {
    Count int
    In    []any
}
```

### func (\*CheckError) Error 

```go
func (s *CheckError) Error() string
```

type Config 
-----------

A Config structure contains options for running a test.

```go
type Config struct {
    // MaxCount sets the maximum number of iterations.
    // If zero, MaxCountScale is used.
    MaxCount int
    // MaxCountScale is a non-negative scale factor applied to the
    // default maximum.
    // A count of zero implies the default, which is usually 100
    // but can be set by the -quickchecks flag.
    MaxCountScale float64
    // Rand specifies a source of random numbers.
    // If nil, a default pseudo-random source will be used.
    Rand *rand.Rand
    // Values specifies a function to generate a slice of
    // arbitrary reflect.Values that are congruent with the
    // arguments to the function being tested.
    // If nil, the top-level Value function is used to generate them.
    Values func([]reflect.Value, *rand.Rand)
}
```

type Generator 
--------------

A Generator can generate random values of its own type.

```go
type Generator interface {
    // Generate returns a random instance of the type on which it is a
    // method using the size as a size hint.
    Generate(rand *rand.Rand, size int) reflect.Value
}
```

type SetupError 
---------------

A SetupError is the result of an error in the way that check is being
used, independent of the functions being tested.

```go
type SetupError string
```

### func (SetupError) Error 

```go
func (s SetupError) Error() string
```

 
© Google, Inc.\
Licensed under the Creative Commons Attribution License 3.0.\
https://golang.org/pkg/testing/quick/>


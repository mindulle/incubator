Package elliptic
================

-   `import "crypto/elliptic"`
-   [Overview](#pkg-overview)
-   [Index](#pkg-index)

Overview 
--------

Package elliptic implements the standard NIST P-224, P-256, P-384, and
P-521 elliptic curves over prime fields.

Direct use of this package is deprecated, beyond the [P224](#P224),
[P256](#P256), [P384](#P384), and [P521](#P521) values necessary to use
crypto/ecdsa. Most other uses should migrate to the more efficient and
safer crypto/ecdh, or to third-party modules for lower-level
functionality.

Index 
-----

-   [func GenerateKey(curve Curve, rand io.Reader) (priv \[\]byte, x, y
    \*big.Int, err error)](#GenerateKey)
-   [func Marshal(curve Curve, x, y \*big.Int) \[\]byte](#Marshal)
-   [func MarshalCompressed(curve Curve, x, y \*big.Int)
    \[\]byte](#MarshalCompressed)
-   [func Unmarshal(curve Curve, data \[\]byte) (x, y
    \*big.Int)](#Unmarshal)
-   [func UnmarshalCompressed(curve Curve, data \[\]byte) (x, y
    \*big.Int)](#UnmarshalCompressed)
-   [type Curve](#Curve)
-   [func P224() Curve](#P224)
-   [func P256() Curve](#P256)
-   [func P384() Curve](#P384)
-   [func P521() Curve](#P521)
-   [type CurveParams](#CurveParams)
-   [func (curve \*CurveParams) Add(x1, y1, x2, y2 \*big.Int)
    (\*big.Int, \*big.Int)](#CurveParams.Add)
-   [func (curve \*CurveParams) Double(x1, y1 \*big.Int) (\*big.Int,
    \*big.Int)](#CurveParams.Double)
-   [func (curve \*CurveParams) IsOnCurve(x, y \*big.Int)
    bool](#CurveParams.IsOnCurve)
-   [func (curve \*CurveParams) Params()
    \*CurveParams](#CurveParams.Params)
-   [func (curve \*CurveParams) ScalarBaseMult(k \[\]byte) (\*big.Int,
    \*big.Int)](#CurveParams.ScalarBaseMult)
-   [func (curve \*CurveParams) ScalarMult(Bx, By \*big.Int, k \[\]byte)
    (\*big.Int, \*big.Int)](#CurveParams.ScalarMult)

### Package files

elliptic.go nistec.go nistec\_p256.go params.go

func GenerateKey 
----------------

```go
func GenerateKey(curve Curve, rand io.Reader) (priv []byte, x, y *big.Int, err error)
```

GenerateKey returns a public/private key pair. The private key is
generated using the given reader, which must return random data.

Deprecated: for ECDH, use the GenerateKey methods of the crypto/ecdh
package; for ECDSA, use the GenerateKey function of the crypto/ecdsa
package.

func Marshal 
------------

```go
func Marshal(curve Curve, x, y *big.Int) []byte
```

Marshal converts a point on the curve into the uncompressed form
specified in SEC 1, Version 2.0, Section 2.3.3. If the point is not on
the curve (or is the conventional point at infinity), the behavior is
undefined.

Deprecated: for ECDH, use the crypto/ecdh package. This function returns
an encoding equivalent to that of PublicKey.Bytes in crypto/ecdh.

func MarshalCompressed 
-------------------------------------------------------

```go
func MarshalCompressed(curve Curve, x, y *big.Int) []byte
```

MarshalCompressed converts a point on the curve into the compressed form
specified in SEC 1, Version 2.0, Section 2.3.3. If the point is not on
the curve (or is the conventional point at infinity), the behavior is
undefined.

func Unmarshal 
--------------

```go
func Unmarshal(curve Curve, data []byte) (x, y *big.Int)
```

Unmarshal converts a point, serialized by Marshal, into an x, y pair. It
is an error if the point is not in uncompressed form, is not on the
curve, or is the point at infinity. On error, x = nil.

Deprecated: for ECDH, use the crypto/ecdh package. This function accepts
an encoding equivalent to that of the NewPublicKey methods in
crypto/ecdh.

func UnmarshalCompressed 
---------------------------------------------------------

```go
func UnmarshalCompressed(curve Curve, data []byte) (x, y *big.Int)
```

UnmarshalCompressed converts a point, serialized by MarshalCompressed,
into an x, y pair. It is an error if the point is not in compressed
form, is not on the curve, or is the point at infinity. On error, x =
nil.

type Curve 
----------

A Curve represents a short-form Weierstrass curve with a=-3.

The behavior of Add, Double, and ScalarMult when the input is not a
point on the curve is undefined.

Note that the conventional point at infinity (0, 0) is not considered on
the curve, although it can be returned by Add, Double, ScalarMult, or
ScalarBaseMult (but not the Unmarshal or UnmarshalCompressed functions).

Using Curve implementations besides those returned by P224(), P256(),
P384(), and P521() is deprecated.

```go
type Curve interface {
    // Params returns the parameters for the curve.
    Params() *CurveParams

    // IsOnCurve reports whether the given (x,y) lies on the curve.
    //
    // Deprecated: this is a low-level unsafe API. For ECDH, use the crypto/ecdh
    // package. The NewPublicKey methods of NIST curves in crypto/ecdh accept
    // the same encoding as the Unmarshal function, and perform on-curve checks.
    IsOnCurve(x, y *big.Int) bool

    // Add returns the sum of (x1,y1) and (x2,y2).
    //
    // Deprecated: this is a low-level unsafe API.
    Add(x1, y1, x2, y2 *big.Int) (x, y *big.Int)

    // Double returns 2*(x,y).
    //
    // Deprecated: this is a low-level unsafe API.
    Double(x1, y1 *big.Int) (x, y *big.Int)

    // ScalarMult returns k*(x,y) where k is an integer in big-endian form.
    //
    // Deprecated: this is a low-level unsafe API. For ECDH, use the crypto/ecdh
    // package. Most uses of ScalarMult can be replaced by a call to the ECDH
    // methods of NIST curves in crypto/ecdh.
    ScalarMult(x1, y1 *big.Int, k []byte) (x, y *big.Int)

    // ScalarBaseMult returns k*G, where G is the base point of the group
    // and k is an integer in big-endian form.
    //
    // Deprecated: this is a low-level unsafe API. For ECDH, use the crypto/ecdh
    // package. Most uses of ScalarBaseMult can be replaced by a call to the
    // PrivateKey.PublicKey method in crypto/ecdh.
    ScalarBaseMult(k []byte) (x, y *big.Int)
}
```

### func P224 

```go
func P224() Curve
```

P224 returns a Curve which implements NIST P-224 (FIPS 186-3, section
D.2.2), also known as secp224r1. The CurveParams.Name of this Curve is
\"P-224\".

Multiple invocations of this function will return the same value, so it
can be used for equality checks and switch statements.

The cryptographic operations are implemented using constant-time
algorithms.

### func P256 

```go
func P256() Curve
```

P256 returns a Curve which implements NIST P-256 (FIPS 186-3, section
D.2.3), also known as secp256r1 or prime256v1. The CurveParams.Name of
this Curve is \"P-256\".

Multiple invocations of this function will return the same value, so it
can be used for equality checks and switch statements.

The cryptographic operations are implemented using constant-time
algorithms.

### func P384 

```go
func P384() Curve
```

P384 returns a Curve which implements NIST P-384 (FIPS 186-3, section
D.2.4), also known as secp384r1. The CurveParams.Name of this Curve is
\"P-384\".

Multiple invocations of this function will return the same value, so it
can be used for equality checks and switch statements.

The cryptographic operations are implemented using constant-time
algorithms.

### func P521 

```go
func P521() Curve
```

P521 returns a Curve which implements NIST P-521 (FIPS 186-3, section
D.2.5), also known as secp521r1. The CurveParams.Name of this Curve is
\"P-521\".

Multiple invocations of this function will return the same value, so it
can be used for equality checks and switch statements.

The cryptographic operations are implemented using constant-time
algorithms.

type CurveParams 
----------------

CurveParams contains the parameters of an elliptic curve and also
provides a generic, non-constant time implementation of Curve.

The generic Curve implementation is deprecated, and using custom curves
(those not returned by P224(), P256(), P384(), and P521()) is not
guaranteed to provide any security property.

```go
type CurveParams struct {
    P       *big.Int // the order of the underlying field
    N       *big.Int // the order of the base point
    B       *big.Int // the constant of the curve equation
    Gx, Gy  *big.Int // (x,y) of the base point
    BitSize int      // the size of the underlying field
    Name    string   // the canonical name of the curve; added in Go 1.5
}
```

### func (\*CurveParams) Add 

```go
func (curve *CurveParams) Add(x1, y1, x2, y2 *big.Int) (*big.Int, *big.Int)
```

Add implements Curve.Add.

Deprecated: the CurveParams methods are deprecated and are not
guaranteed to provide any security property. For ECDH, use the
crypto/ecdh package. For ECDSA, use the crypto/ecdsa package with a
Curve value returned directly from P224(), P256(), P384(), or P521().

### func (\*CurveParams) Double 

```go
func (curve *CurveParams) Double(x1, y1 *big.Int) (*big.Int, *big.Int)
```

Double implements Curve.Double.

Deprecated: the CurveParams methods are deprecated and are not
guaranteed to provide any security property. For ECDH, use the
crypto/ecdh package. For ECDSA, use the crypto/ecdsa package with a
Curve value returned directly from P224(), P256(), P384(), or P521().

### func (\*CurveParams) IsOnCurve 

```go
func (curve *CurveParams) IsOnCurve(x, y *big.Int) bool
```

IsOnCurve implements Curve.IsOnCurve.

Deprecated: the CurveParams methods are deprecated and are not
guaranteed to provide any security property. For ECDH, use the
crypto/ecdh package. For ECDSA, use the crypto/ecdsa package with a
Curve value returned directly from P224(), P256(), P384(), or P521().

### func (\*CurveParams) Params 

```go
func (curve *CurveParams) Params() *CurveParams
```

### func (\*CurveParams) ScalarBaseMult 

```go
func (curve *CurveParams) ScalarBaseMult(k []byte) (*big.Int, *big.Int)
```

ScalarBaseMult implements Curve.ScalarBaseMult.

Deprecated: the CurveParams methods are deprecated and are not
guaranteed to provide any security property. For ECDH, use the
crypto/ecdh package. For ECDSA, use the crypto/ecdsa package with a
Curve value returned directly from P224(), P256(), P384(), or P521().

### func (\*CurveParams) ScalarMult 

```go
func (curve *CurveParams) ScalarMult(Bx, By *big.Int, k []byte) (*big.Int, *big.Int)
```

ScalarMult implements Curve.ScalarMult.

Deprecated: the CurveParams methods are deprecated and are not
guaranteed to provide any security property. For ECDH, use the
crypto/ecdh package. For ECDSA, use the crypto/ecdsa package with a
Curve value returned directly from P224(), P256(), P384(), or P521().

 
© Google, Inc.\
Licensed under the Creative Commons Attribution License 3.0.\
https://golang.org/pkg/crypto/elliptic/>


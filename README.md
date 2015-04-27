# DecFP: IEEE Decimal Floating-point in Julia

The DecFP package is a Julia wrapper around the [Intel Decimal
Floating-Point Math
Library](https://software.intel.com/en-us/articles/intel-decimal-floating-point-math-library),
providing a software implementation of the IEEE 754-2008 Decimal
Floating-Point Arithmetic specification.

32-bit, 64-bit, and 128-bit decimal floating-point types `Dec32`,
`Dec64`, and `Dec128`, respectively, are provided.  This is very
different from packages such as
[Decimals.jl](https://github.com/tinybike/Decimals.jl), which provide
*arbitrary-precision* decimal types analogous to `BigFloat`: arbitrary
precision types are very flexible, but fixed-precision types such
as those in DecFP are much faster (though still vastly slower than
the hardware binary floating-point types `Float32` and `Float64`).

This is currently a work in progress.

## Usage

`Dec64` and the other types mentioned above can be constructed from
other Julia numeric types, e.g. binary floating-point types via
`Dec64(3.0)`, from strings by `parse(Dec64, "3.2")` or `d64"3.2"` (a
Julia string macro); similarly for `Dec32` and `Dec128`.  The string
macro `d"3.2"` constructs `Dec64`.

Once a decimal float is constructed, most Julia arithemetic and
special functions should work without modification.  For example,
`d"3.2" * d"4.5"` produces the `Dec64` result `+1440E-2` (14.4).
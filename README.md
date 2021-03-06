# kalk
[![Crates.io](https://img.shields.io/crates/v/kalk_cli)](https://crates.io/crates/kalk_cli)
[![GitHub](https://img.shields.io/github/license/PaddiM8/kalk)](https://github.com/PaddiM8/kalk/blob/master/LICENSE)
[![Docs.rs](https://docs.rs/kalk/badge.svg)](https://docs.rs/kalk/latest/kalk/)
![Build status](https://img.shields.io/travis/PaddiM8/kalk/master?label=build%20%26%20test)


Kalk is a calculator (both program and library) that supports user-defined variables, functions, and units (experimental).
[Project kanban board (Kolan)](https://kolan.smrk.me/Board/4RAdMjLDz)

![](example.png)

## Features
* Operators: +, -, \*, /, !
* Groups: (), ⌈⌉, ⌋⌊
* [Pre-defined functions and constants](https://github.com/PaddiM8/kalk/blob/master/kalk/src/prelude.rs)
* User-defined functions and variables. `f(x, y) = xy`, `x = 5`
* User-defined units (experimental). `unit m = cm/100`, `2m/50cm`, `50cm to m`
* Understands fairly ambiguous syntax. Eg. `2sin50 + 2xy`
* Syntax highlighting
* Special-symbol completion on tab. Eg. write `sqrt` and press tab. It will be turned into `√`.
* Sum function: `sum(start, to, expression)` Eg. `sum(1, 3, 2n+1)` is the same as `2*1+1 + 2*2+1 + 2*3+1` = `15`
* Load a file including predefined functions and constants. For example, if you're going to use Kalk for physics, you load up your file with physics functions/constants when starting Kalk. `-i file`
* Misc: separate expressions by a semicolon to write them on the same line, use the `ans` variable to get the value of the previously calculated expression.

## Installing
### Binaries
Pre-compiled binaries for Linux and Windows (64-bit) are available in the [releases page](https://github.com/PaddiM8/kalk/releases). A Windows binary may not always be available for the newest version as of now.
### Compiling
Make sure you have `diffutils` `gcc` `make` and `m4` installed. **If you use windows:** [follow the instructions here](https://docs.rs/gmp-mpfr-sys/1.2.3/gmp_mpfr_sys/index.html#building-on-windows)  
If anyone knows how to get `gmp_mpfr_sys` on Windows on Travis, let me know.

#### Cargo
Run `cargo install kalk_cli`

#### Manually
1. Go into the `kalk_cli` directory.
2. Run `cargo build --release`
3. Grab the binary from `targets/release`

## Syntax

### Functions
__Defining:__ name(parameter1, parameter2, ...) = expression  
**Example:** `f(x) = 2x+3`  

__Using:__ name(argument1, argument2)  
**Example:** `f(2)`  

### Variables
__Defining:__ name = expression  
**Example:** `x = 3`  

__Using:__ name  
**Example:** `x`  

### Units
*Note: You only need to define the relationship between two units once. You will be able to convert between both of them.*
__Defining:__ `unit` name = expression  
**Example:** `unit deg = (rad*180)/π`  

__Using:__ Use them freely in expressions.  
**Example:** `2m/50cm`  

__Converting:__ expression `to` unit  
**Example:** `2 m to cm`  

# [[Data Type|Data Types]]
[[Rust Programming Language]] is a *statically* typed language, which means that it must know the types of all variables at compile time. The compiler can usually infer what type we want to use based on the value and how we use it.

## Scalar Types
A *scalar types* represents a single value.
Rust has four primary scalar types: 
- Integers
- Floating-point numbers
- Booleans
- Characters

### Integer Types
This type declaration indicates that the value it’s associated with should be an unsigned integer, signed integer types start with `i` instead of `u`,

| Length  | Signed | Unsigned |
| ------- | ------ | -------- |
| 8-bit   | i8     | u8       |
| 16-bit  | i16    | u16      |
| 32-bit  | i32    | u32      |
| 65-bit  | i64    | u64      |
| 128-bit | i128   | u128     |
| arch    | isize  | usize    |

```Rust
let guess: u32 = 42
```

Signed numbers are stored using [[Two's complement|two’s complement]] representation.

Each signed variant can store numbers from ${-(2^{n-1})}$ to ${(2^{n-1}-1)}$ inclusive, where *n* is the number of bits that variant uses.

Additionally, the `isize` and `usize` types depend on the architecture of the computer your program is running on, which is denoted in the table as “arch”: 64 bits if you’re on a 64-bit architecture and 32 bits if you’re on a 32-bit architecture.

#### Integer Overflow
Let’s say you have a variable of type `u8` that can hold values between 0 and 255. If you try to change the variable to a value outside that range, such as 256, _integer overflow_ will occur, which can result in one of two behaviors.

When you’re compiling in debug mode, Rust includes checks for integer overflow that cause your program to [[Panic|panic]] at runtime if this behavior occurs.

### Floating-Point Types
Rust’s floating-point types are `f32` and `f64`, which are 32 bits and 64 bits in size, respectively.

The `f32` type is a single-precision float, and `f64` has double precision.

```Rust
fn main() {
	let x = 2.0; // f64
	let y: f32 = 3.0; // f32
}
```

Floating-point numbers are represented according to the [[IEEE-754 standard]].

### Numeric Operations
Rust supports the basic mathematical operations for all the number types: addition, subtraction, multiplication, division, and remainder.

```Rust
fn main() {
    // addition
    let sum = 5 + 10;

    // subtraction
    let difference = 95.5 - 4.3;

    // multiplication
    let product = 4 * 30;

    // division
    let quotient = 56.7 / 32.2;
    let truncated = -5 / 3; // Results in -1

    // remainder
    let remainder = 43 % 5;
}
```

### The Boolean Type
Boolean type is Rust has two possible values: `true` and `false`. Booleans are one byte in size.

The Boolean type in Rust is specified using `bool`.

For example:
```Rust
fn main() {
	let t = true;

	let f: bool = false; // with explicit type annotation.
}
```

### The Character Type
Rust's `char` type is the language's most primitive alphabetic type. 

```Rust
fn main() {
    let c = 'z';
    let z: char = 'ℤ'; // with explicit type annotation
    let heart_eyed_cat = '😻';
}
```

> Note that we specify `char` literals with single quotes, as opposed to string literals, which use double quotes.

Rust’s `char` type is four bytes in size and represents a Unicode Scalar Value, which means it can represent a lot more than just ASCII.

Accented letters; Chinese, Japanese, and Korean characters; emoji; and zero-width spaces are all valid `char` values in Rust.

## Compound Types
*Compound types* can group multiple values intro one type. 

Rust has two primitive compound types:
- tuples
- arrays

### The Tuple Type
A tuple is a general way of grouping a number of values with a variety of types into one compound type.

> Tuples have a fixed length: once declared, they cannot grow or shrink in size.

Tuples are created by writing a comma-separated list of values inside parentheses. Each position in the tuple has a type, and the types of the different values in the tuple don't have to be the same.

```Rust
fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
}
```

The variable `tup` binds to the entire tuple because a tuple is considered a single compound element.

To get the individual values out of a tuple, we can use pattern matching to destructure a tuple value, like this:

```Rust
fn main() {
    let tup = (500, 6.4, 1);

    let (x, y, z) = tup;

    println!("The value of y is: {y}");
}
```

This program first creates a tuple and binds it to the variable `tup`. It then uses a pattern with `let` to take `tup` and turn it into three separate variables, `x`, `y`, and `z`. This is called _destructuring_ because it breaks the single tuple into three parts. Finally, the program prints the value of `y`, which is `6.4`.
A tuple element can be directly accessed by using a period (`.`) followed by the index of the value.

For example:
```Rust
fn main() {
	let x: (i32, f64, u8) = (500, 6.4, 1);
	let five_hundred = x.0;
	let six_point_four = x.1;
	let one = x.2;
}
```

This program creates the tuple `x` and then accesses each element of the tuple using their respective indices. As with most programming languages, the first index in a tuple is 0.

> The tuple without any values has a special name, *unit*.

This value and its corresponding type are both written `()` and represent an empty value or an empty return type. Expressions implicitly return the unit value if they don’t return any other value.

### The Array Type
Array is a collection of multiple values.
- Arrays must have same type.
- Arrays must have fixed length.

```Rust
fn main() {
	let a = [1, 2, 3, 4, 5]
}
```

Array declared using brackets with the type of each element, a semicolon, and then the number of elements in the array, like so:

```Rust
let a: [i32; 5] = [1, 2, 3, 4, 5];
```

Arrays can be initialized to contain the same value for each element by specifying the initial value, followed by a semicolon, and then the length of the array in square brackets, as shown here:

```Rust
let a = [3; 5];
```

#### Accessing Array Elements
An array is a single chunk of memory of a known, fixed size that can be allocated on the [[Stack]]. You can access elements of an array using indexing, like this:

```Rust
fn main() {
	let a = [1, 2, 3, 4, 5];
	let first = a[0];
	let second = a[1];
}
```

#### Invalid Array Element Access
If an element that is past the end of the array is accessed, code will compile successfully. But if number past the end of the array is entered the program will result in error. 
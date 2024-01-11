# Slice
In [[Rust Programming Language|rust]], *Slice* - a dynamically-sized view into a contiguous sequence.

## String Slices
A *string slice* is a [[Rust - References and Borrowing|reference]] to part of a `String`, and it looks like this:
```Rust
let s = String::from("hello world");
let hello = &s[0..5];
let world = &s[6..11];
```
Rather than a reference to the entire `String`, `hello` is a reference to a portion of the `String`, specified in the extra `[0..5]` bit. We create slices using a range within brackets by specifying `[starting_index..ending_index]`, where `starting_index` is the first position in the slice and `ending_index` is one more than the last position in the slice.
![[Pasted image 20240111150142.png]]

With Rust’s `..` range syntax, if you want to start at index 0, you can drop the value before the two periods. In other words, these are equal:
```Rust
let s = String::from("hello");
let slice = &s[0..2];
let slice = &s[..2];
```
By the same token, if your slice includes the last byte of the `String`, you can drop the trailing number. That means these are equal:
```Rust
let s = String::from("hello");

let len = s.len();

let slice = &s[3..len];
let slice = &s[3..];
```
You can also drop both values to take a slice of the entire string. So these are equal:
let s = String::from("hello");
```Rust
let len = s.len();

let slice = &s[0..len];
let slice = &s[..];
```

> [!info]
> The type that signifies “string slice” is written as `&str`

## String Literals as Slices

## String Slices as Parameters

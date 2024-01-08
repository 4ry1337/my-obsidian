# Variables and Mutability
By default variables are immutable, because:
- Safety
- Concurrency
When a variable is immutable, once a value is bound to a name, you can’t change that value.
```Rust
fn main() {
	let x = 5;
	println!("The value of x is: {x}");
	x = 6;
	println!("The value of x is: {x}");
}
```
Although, variables can be mutable ny adding `mut` in front of the variable name.
```Rust
fn main() {
	let mut x = 5;
	println!("The value of x is: {x}");
	x = 6;
	println!("The value of x is: {x}");
}
```
## Constants
Constants are values that are bound to a name and not allowed to change.

Difference between constants and variables:
- Not allowed to use `mut` with constants.
- Can be declared in any scope, including the global scope.
- May be set only to a constant expression, not the result of a value that could only be computed at runtime.

*Constants aren’t just immutable by default—they’re always immutable.* Constants declared using the `const` keyword instead of the `let` keyword, and the type of the value *must* be annotated.

Here’s an example of a constant declaration:

```Rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```

The constant’s name is `THREE_HOURS_IN_SECONDS` and its value is set to the result of multiplying 60 (the number of seconds in a minute) by 60 (the number of minutes in an hour) by 3 (the number of hours we want to count in this program).

Rust’s naming convention for constants is to use all uppercase with underscores between words.

Constants are valid for the entire time a program runs, within the scope in which they were declared.

## Shadowing
In effect, the second variable overshadows the first, taking any uses of the variable name to itself until either it itself is shadowed or the scope ends.

```Rust
fn main() {
	let x = 5;
	let x = x + 1;
	{
		let x = x * 2;
		println!("The value of x in the inner scope is:{x}");
	}
	println!("The value of x is: {x}");
}
```
This program first binds `x` to a value of `5`. Then it creates a new variable `x` by repeating `let x =`, taking the original value and adding `1` so the value of `x` is then `6`. Then, within an inner scope created with the curly brackets, the third `let` statement also shadows `x` and creates a new variable, multiplying the previous value by `2` to give `x` a value of `12`. When that scope is over, the inner shadowing ends and `x` returns to being `6`.

Shadowing is different from marking a variable as `mut` because we’ll get a compile-time error if we accidentally try to reassign to this variable without using the `let` keyword.

The other difference between `mut` and shadowing is that because we’re effectively creating a new variable when we use the `let` keyword again, we can change the type of the value but reuse the same name.

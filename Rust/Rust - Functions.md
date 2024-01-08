# [[Function|Functions]]
> [!info]
> The `main` function is the entry point of program.

`fn` keyword allows to declare new functions.

Rust code uses [[snake case]] as the conventional style for function and variables names.

Examples:
```Rust
fn main() {
    println!("Hello, world!");

    another_function();
}

fn another_function() {
    println!("Another function.");
}
```

> [!info]
> A function defined in Rust by entering `fn` followed by a function name and a set of parentheses. The curly brackets tell the compiler where the function body begins and ends.

## Parameters
```Rust
fn main() {
    another_function(5);
}

fn another_function(x: i32) {
    println!("The value of x is: {x}");
}
```
The declaration of `another_function` has one [[Parameter|parameter]] named `x`. The type of `x` is specified as `i32`. When we pass `5` in to `another_function`, the `println!` macro puts `5` where the pair of curly brackets containing `x` was in the format string.

In function signatures, you _must_ declare the type of each parameter. This is a deliberate decision in Rust’s design: requiring type annotations in function definitions means the compiler almost never needs you to use them elsewhere in the code to figure out what type you mean.

### Statement and Expression
Function bodies are made up of a series of [[Statement|statements]] optionally ending in an expression.

Rust is an expression-based language

- **Statements** are instructions that perform some action and do not return a value.
- **Expressions** evaluate to a resultant value.

Statements do not return values. Therefore, you can’t assign a `let` statement to another variable, as the following code tries to do; you’ll get an error:

```Rust
fn main() {
	let x = (let y = 6);
}
```

The `let y = 6` statement does not return a value, so there isn’t anything for `x` to bind to. This is different from what happens in other languages, such as [[C Programming Language|C]] and Ruby, where the assignment returns the value of the assignment. In those languages, you can write `x = y = 6` and have both `x` and `y` have the value `6`; that is not the case in Rust.

Calling a function is an expression. Calling a macro is an expression. A new scope block created with curly brackets is an expression, for example:

```Rust
fn main() {
    let y = {
        let x = 3;
        x + 1
    };

    println!("The value of y is: {y}");
}
```

> [!info]
> Expressions do not include ending semicolons. If you add a semicolon to the end of an expression, you turn it into a statement, and it will then not return a value.
 
## Functions with Return Values
Functions can return values to the code that calls them. Return type must be declared after arrow `->`.

> [!info]
> In Rust, the return value of the function is synonymous with the value of the final expression in the block of the body of a function.


# [[Control Flow]]
## `if` Expressions
All `if` expressions start with the keyword `if`, followed by a condition.

Blocks of code associated with the conditions in `if` expressions are sometimes called _arms_.

```Rust
fn main() {
    let number = 3;

    if number < 5 {
        println!("condition was true");
    } else {
        println!("condition was false");
    }
}
```
### Handling Multiple Conditions with `else if`
```Rust
fn main() {
    let number = 6;

    if number % 4 == 0 {
        println!("number is divisible by 4");
    } else if number % 3 == 0 {
        println!("number is divisible by 3");
    } else if number % 2 == 0 {
        println!("number is divisible by 2");
    } else {
        println!("number is not divisible by 4, 3, or 2");
    }
}
```
### Using `if` in a `let` Statement
Because `if` is an expression, it can be used on the right side of a `let` statement to assign the outcome to a variable.

```Rust
fn main() {
    let condition = true;
    let number = if condition { 5 } else { 6 };

    println!("The value of number is: {number}");
}
```

Remember that blocks of code evaluate to the last expression in them, and numbers by themselves are also expressions. In this case, the value of the whole `if` expression depends on which block of code executes. This means the values that have the potential to be results from each arm of the `if` must be the same type.

> Rust needs to know at compile time what type the variable is, definitively.

## Repetition with Loops
Rust has three kinds of loops: `loop`, `while`, and `for`.

The `break` keyword can be placed within the loop to tell the program when to stop executing the loop

The `continue` keyword in a loop tells the program to skip over any remaining code in this iteration of the loop and go to the next iteration.

### Repeating Code with `loop`
The `loop` keyword tells Rust to execute a block of code over and over again forever or until you explicitly tell it to stop.
```Rust
fn main() {
    loop {
        println!("again!");
    }
}
```

#### Returning Values from Loops
```
fn main() {
    let mut counter = 0;
    
    let result = loop {
        counter += 1;
        
        if counter == 10 {
            break counter * 2;
        }
    };
    
    println!("The result is {result}");
}
```

#### Loop Labels to Disambiguate Between Multiple Loops
When loops within loops, `break` and `continue` apply to the innermost loop at that point.

> [!info]
> Optionally loops can be specified with *loop label* that can be used to `break` or `continue` to specify that those keywords apply to the labeled loop instead of the innermost loop.

### Conditional Loop with `while`
```Rust
fn main() {
	let mut number = 3;
	
	while number != 0 {
		println!("{number}!");
		number -= 1;
	}
	
	println!("LIFTOFF!!!");
}
```
### Looping Through a Collection with `for`
```Rust
fn main() {
    let a = [10, 20, 30, 40, 50];

    for element in a {
        println!("the value is: {element}");
    }
}
```

```Rust
fn main() {
    for number in (1..4).rev() {
        println!("{number}!");
    }
    println!("LIFTOFF!!!");
}
```

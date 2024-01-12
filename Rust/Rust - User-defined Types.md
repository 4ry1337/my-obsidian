# User-defined Types
User-defined types are created with the `struct` or `enum` keywords. The `struct` keyword is used to denote a record type that groups multiple related values. `enum`s can take on different variants in runtime, with its capabilities similar to [[Algebraic Data Types|algebraic data types]] found in [[Functional Programming|functional programming]] languages.

Both structs and enums can contain fields with different types. Alternative names for the same type can be defined with the `type` keyword.

The `impl` keyword can define methods for a user-defined type (data and functions are defined separately). Implementations fulfill a role similar to that of classes within other languages.

## Struct
To define a struct, we enter the keyword `struct` and name the entire struct. A struct’s name should describe the significance of the pieces of data being grouped together. Then, inside curly brackets, we define the names and types of the pieces of data, which we call *fields*.

```Rust
struct User {
	active: bool,
	username: String,
	email: String,
	sign_in_count: u64,
}
```

To use a struct after we’ve defined it, we create an _instance_ of that struct by specifying concrete values for each of the fields.

```Rust
fn main() {
    let user1 = User {
        active: true,
        username: String::from("someusername123"),
        email: String::from("someone@example.com"),
        sign_in_count: 1,
    };
}
```

To get a specific value from a struct, we use dot notation. For example, to access this user’s email address, we use `user1.email`. If the instance is mutable, we can change a value by using the dot notation and assigning into a particular field.

```Rust
fn main() {
    let mut user1 = User {
        active: true,
        username: String::from("someusername123"),
        email: String::from("someone@example.com"),
        sign_in_count: 1,
    };

    user1.email = String::from("anotheremail@example.com");
}
```

> [!info]
> Note that the entire instance must be mutable; Rust doesn’t allow us to mark only certain fields as mutable.

As with any expression, we can construct a new instance of the struct as the last expression in the function body to implicitly return that new instance.

```Rust
fn build_user(email: String, username: String) -> User {
	User {
		active: true,
		username: username,
		email: email,
		sign_in_count: 1,
	}
}
```

### Using the Field Init Shorthand
Because the parameter names and the struct field names are exactly the same, we can use the _field init shorthand_ syntax to rewrite `build_user` so it behaves exactly the same but doesn’t have the repetition of `username` and `email`.

```Rust
fn build_user(email: String, username: String) -> User {
    User {
        active: true,
        username,
        email,
        sign_in_count: 1,
    }
}
```

### Creating Instances from Other Instances with Struct Update Syntax
It’s often useful to create a new instance of a struct that includes most of the values from another instance, but changes some. You can do this using _struct update syntax_.
```Rust
fn main() {
    // --snip--

    let user2 = User {
        active: user1.active,
        username: user1.username,
        email: String::from("another@example.com"),
        sign_in_count: user1.sign_in_count,
    };
}
```

```Rust
fn main() {
    // --snip--

    let user2 = User {
        email: String::from("another@example.com"),
        ..user1
    };
}
```

> [!info]
> Note that the struct update syntax uses `=` like an assignment; this is because it moves the data.

See [[Rust - Ownership#Variables and Data Interacting with Move]]

In this example, we can no longer use `user1` as a whole after creating `user2` because the `String` in the `username` field of `user1` was moved into `user2`.

See [[Rust - Ownership#Stack-Only Data Copy]]

### Using Tuple Structs Without Named Fields to Create Different Types

[[Rust Programming Language|Rust]] also supports structs that look similar to tuples, called *tuple structs*.

Tuple structs have the added meaning the struct name provides but don’t have names associated with their fields; rather, they just have the types of the fields.

```Rust
struct Color(i32, i32, i32);
struct Point(i32, i32, i32);
fn main() {
	let black = Color(0, 0, 0);
	let origin = Point(0, 0, 0);
}
```

### Unit-Like Structs Without Any Fields
*Unit-like structs* don’t have any fields, similar to [[Rust - Data Types#The Tuple Type|`()`]].

```Rust
struct AlwaysEqual;
fn main() {
	let subject = AlwaysEqual;
}
```
### Ownership of Struct Data
In the `User` struct definition, we used the owned `String` type rather than the `&str` string slice type. This is a deliberate choice because we want each instance of this struct to own all of its data and for that data to be valid for as long as the entire struct is valid.

It’s also possible for structs to store references to data owned by something else, but to do so requires the use of [[Rust - Lifetimes|_lifetimes_]]
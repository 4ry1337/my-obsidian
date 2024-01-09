# Reference
A *reference* is a like a pointer in that it's an address we can follow to access the data stored at the address; that data is owned by some other variable. Unlike a pointer, a reference is guaranteed to point to a valid value of a particular type for the life of that reference.

> [!info]
> The opposite of referencing by using `&` is *dereferencing*, which is accomplished with the dereference operator, `*`.

Let’s take a closer look at the function call here:
```Rust
    let s1 = String::from("hello");
    let len = calculate_length(&s1);
    
    fn calculate_length(s: &String) -> usize { // s is a reference to a String
	    s.len()
    }
    // Here, s goes out of scope. But because it does not have ownership of what
    // it refers to, it is not dropped.
```
The `&s1` syntax lets us create a reference that *refers* to the value of `s1` but does not own it. Because it does not own it, the value it points to will not be dropped when the reference stops being used.

## Borrowing

The action of creating a reference *borrowing*. Reference as variables are immutable by default. We’re not allowed to modify something we have a reference to.

## Mutable References
We create a mutable reference with `&mut`. Mutable references have one big restriction: if you have a mutable reference to a value, you can have no other references to that value.

 The benefit of having this restriction is that Rust can prevent data races at compile time. A _data race_ is similar to a race condition and happens when these three behaviors occur:

- Two or more pointers access the same data at the same time.
- At least one of the pointers is being used to write to the data.
- There’s no mechanism being used to synchronize access to the data.

Data races cause undefined behavior and can be difficult to diagnose and fix when you’re trying to track them down at runtime; Rust prevents this problem by refusing to compile code with data races!

As always, we can use curly brackets to create a new scope, allowing for multiple mutable references, just not _simultaneous_ ones.

We _also_ cannot have a mutable reference while we have an immutable one to the same value.

```Rust
    let mut s = String::from("hello");

    let r1 = &s; // no problem
    let r2 = &s; // no problem
    let r3 = &mut s; // BIG PROBLEM

    println!("{}, {}, and {}", r1, r2, r3);
```

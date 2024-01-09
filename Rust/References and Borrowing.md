A *reference* is a like a pointer in that it's an address we can follow to access the data stored at the address; that data is owned by some other variable. Unlike a pointer, a reference is guaranteed to point to a valid value of a particular type for the life of that reference.

> [!info]
> The opposite of referencing by using `&` is *dereferencing*, which is accomplished with the dereference operator, `*`.

Let’s take a closer look at the function call here:
```Rust
    let s1 = String::from("hello");
    let len = calculate_length(&s1);
```
The `&s1` syntax lets us create a reference that *refers* to the value of `s1` but does not own it. Because it does not own it, the value it points to will not be dropped when the reference stops being used.
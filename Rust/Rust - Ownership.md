# Ownership
**Ownership** is a set of rules that govern how a [[Rust Programming Language|Rust]] program manages memory.

> [!info]
> Memory is managed through a system of ownership with a set of rules that the compiler checks.

## Rules
- Each value in Rust has an owner.
- There can only be one owner at a time.
- When the owner goes out of scope, the value will be dropped.

## Variable Scope
A scope is the range within a program for which an item is valid.

## Memory and Allocation
Rust deallocates resources at the item's lifetime, i.e. the memory is automatically returned once the variable that owns it goes out of scope. This is sometimes called [[Resource Acquisition is Initialization (RAII)]].

### Variables and Data Interacting with Move
In rust, if data is unknown size, like integer, strings, for example, when we reassign it to some different value, the is being *moved*. So:
```Rust
let s1 = String::from("hello");
let s2 = s1;
```
s1 is assigned String Hello. Then s1 is assigned to s2, which moves only data to s2, thus making s1 invalid.

![[Pasted image 20231226112431.png]]
![[Pasted image 20231226112435.png]]

### Variables and Data Interacting with Clone
If we _do_ want to deeply copy the heap data of the `String`, not just the stack data, we can use a common method called `clone`.
```Rust
    let s1 = String::from("hello");
    let s2 = s1.clone();

    println!("s1 = {}, s2 = {}", s1, s2);
```
#### Stack-Only Data: Copy
There’s another wrinkle we haven’t talked about yet. 

```Rust
let x = 5;
let y = x;
println!("x = {}, y = {}", x, y);
```

But this code seems to contradict what we just learned: we don’t have a call to `clone`, but `x` is still valid and wasn’t moved into `y`.

The reason is that types such as integers that have a known size at compile time are stored entirely on the stack, so copies of the actual values are quick to make. That means there’s no reason we would want to prevent `x` from being valid after we create the variable `y`.

There’s no difference between [[deep]] and [[shallow copying]] here, so calling `clone` wouldn’t do anything different from the usual shallow copying, and we can leave it out.

## Ownership and Functions
Passing a variable to a function will move and copy, just as assignment does. If we tried to use variable after the call to function, Rust would throw a compile-time error.

### Return values and Scope
Returning values can also transfer ownership. The ownership of a variable follows the same pattern every time: assigning a value to another variable moves it.

When a variable that includes data on the heap goes out of scope, the value will be cleaned up by `drop` unless ownership of the data has been moved to another variable.


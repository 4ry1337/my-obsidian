# User-defined Types
User-defined types are created with the `struct` or `enum` keywords. The `struct` keyword is used to denote a record type that groups multiple related values. `enum`s can take on different variants in runtime, with its capabilities similar to [[Algebraic Data Types|algebraic data types]] found in [[Functional Programming|functional programming]] languages.

Both structs and enums can contain fields with different types. Alternative names for the same type can be defined with the `type` keyword.

The `impl` keyword can define methods for a user-defined type (data and functions are defined separately). Implementations fulfill a role similar to that of classes within other languages.

## Struct
To define a struct, we enter the keyword `struct` and name the entire struct. A struct’s name should describe the significance of the pieces of data being grouped together. Then, inside curly brackets, we define the names and types of the pieces of data, which we call *fields*.
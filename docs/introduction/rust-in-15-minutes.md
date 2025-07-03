# Rust In 15 Minutes

Examples showing the syntax and basic concepts of the Rust programming language.  Consider this a sneak peak for the rest of the book.

> NOTE: [Rust Tutorial video series](https://youtube.com/playlist?list=PLLqEtX6ql2EyPAZ1M2_C0GgVd4A-_L4_5&si=xK0jSgNZgZAyitOy) provides an in-depth introduction to Rust (or read the rest of this book)


## Local variables

Assign a value to a local variable using `let` inside a function or procedure


```rust
fn main() {
  let myName = "Nishant"; // Rust infers type to be String
  let coins: u32 = 4; // explicit type, unsigned 32-bit integer

  let age = 19; // number defaults to i32 type, signed 32-bit integer
}
```

Variables are immutable unless the `mut` type is explicitly included


```rust
fn main() {
  let mut age = 21;
}
```

> NOTE: rust compiler will warn if a variable doesnt need to be mutable or if it is unused.

> NOTE: use `const` for a 'shared' variable

If we declare a variable, and we try to use it without initializing, the Rust compiler will complain.

```rust
// * WILL NOT COMPILE
fn main() {
  let coins: u32;
  foobar(coins);
}

fn foobar(num: u32) {
  println!("The number sent was {}", num);
}
```

```shell-output
Compiling hello_cargo v0.1.0 (/home/nishant/Programming/Rust/hello_cargo)
error[E0381]: used binding `coins` isn't initialized
 --> src/main.rs:3:9
  |
2 |     let coins: u32;
  |         ----- binding declared here but left uninitialized
3 |     foobar(coins);
  |            ^^^^^ `coins` used here but it isn't initialized
  |
help: consider assigning a value
  |
2 |     let coins: u32 = 0;
  |                    +++

For more information about this error, try `rustc --explain E0381`.
error: could not compile `hello_cargo` due to previous error
```

As Rust programmers, we must read all error messages fully. The error message here tells us that we have used coins but we haven’t initialized it. The message goes on to say that in line 2, we should append = 0 in order for the code to work!

There are many data types used in Rust. We have come across String, i32 and u32. We also have,

```rust
fn main() {
  let temperature: f32 = 6.4;
  let circumference: f64 = 23053.7106;

  let grade: char = 'A';
  let pass: bool = true;
}
```

### Mutation

All symbols are immutable unless marked with `mut` for mutation.

When a symbol is declared mutable, care should be taken to assign it of the same type.


### Constants

```rust
const welcome_message = "Welcome to the wonderful world of Rust";
```

[Constant items - Rust-Lang](https://doc.rust-lang.org/reference/items/constant-items.html){target=_blank .md-button}


## Compound data types

Those above were some more primitive data types. Rust has support for compound data types as well!

```rust
fn main() {
  let pair = ('A', 65);

  println!(pair.0) // Accessing first element
  println!(pair.1) // Accessing second element

  // Destructuring a pair.
  let (letter, number) = pair
}
```

The implicit type for pair is (char, i32). Tuples are heterogeneous and can support nested tuples as well.

Additionally, we can work with Arrays as well,

```rust
fn main() {
  let a = [1, 2, 3, 4, 5];
  // a has a type [i32; 5] - an array of five signed 32-bit integers.
}
```

A data type declaration can hint towards a quick way to initialize arrays.

```rust
fn main() {
  let a = [3; 5];

  for i in a {
    println!("{i}");
  }
}

// This program will print 3 on five lines.
```


## Functions

We have seen we have been using the main function to denote the starting point in our program. The syntax of defining functions is

```rust
fn <function-name>(<param-name>: <param-type>) -> <return-type> {
  body
}

An example function can be like:

fn is_divisible(num: i32, dividend: i32) -> bool {
  num % dividend == 0
}
```

Notice I do not have a semicolon at the end of that statement. This signifies that the expression will return a particular value. If I add a semicolon, Rust will treat the expression as a statement and will complain I am not returning a boolean value.

### Procedures

Procedures are functions that do not return a value

<!-- TODO: check code correctness -->

```rust
fn <Procedure-name>(<param-name>: <param-type>) {
  body
}

An example function can be like:

fn output_results(num: i32, dividend: i32) {
    println!(num % dividend == 0);
}
```


## Let Expressions

Combining the knowledge of variables and functions, we can assign values like this:

```rust
let x = {
  let y = 1;
  let z = 2;

  y + z // Note the lack of semicolon to indicate return value
}
```

Hence, we can conclude that:

```rust
fn main() {
  let x = 0;
  let x = { 0 }; // these two are the same!
}
```

## Variable Shadowing and Scopes

Notice how I didn’t prefix the previous code block with // * WILL NOT COMPILE. However, I do have two declarations of the same variable. This is called variable shadowing.

```rust
fn main() {
  let x = 0;
  let x = { 10 }; // shadowed the previous value of x
}
```

First we initialize x to be 0, and then I am re-initializing it to be 10. This is a valid program and useful in many ways when we couple it with scopes!

Scopes are just a block of code where shadowed variables do not affect the value of the variable outside the scope.

```rust
fn main () {
  let x = 4;

  {
    let x = "shadowing x";
    println!("{}", x); // pfints "shadowing x"
  }

  println!("{}", x); // prints "4"
}
```

## Namespaces

If we wish to use functions from other libraries, we can use namespaces.

```rust
fn main() {
  let least = std::cmp::min(3, 8);

  println!("{}", least);
}
```

We can also bring the function into scope by using the use keyword.

```rust
use std::cmp::min;

fn main() {
  let least = min(3, 8);

  println!("{}", least);
}
```

Use `std::cmp::*` to bring every function inside `std::cmp` into scope.


## Structs

Define a struct Coordinate and initialize a variable of that type.

```rust
struct Coordinate {
  x: f64,
  y: f64
}

fn main() {
  let somewhere = Coordinate { x: 23, y: 3.5 };

  // Spreading the values of somewhere and updating x to 5.4
  // make sure that ..somewhere is at the end.
  let elsewhere = Coordinate { x: 5.4, ..somwhere };

  // Destructuring Coordinate.
  let Coordinate {
    x,
    y
  } = elsewhere;
}
```

Implement a functions for the struct

```rust
impl Coordinate {
  fn add(self, coord: Coordinate) -> Coordinate {
    let newX = self.x + coord.x;
    let newY = self.y + coord.y;

    Coordinate { x: newX, y: newY }
  }
}
```


## Pattern Matching

Pattern Matching is like a conditional structure.

```rust
fn main() {
  let coordinate = Coordinate { x: 3.0, y: 5.0 }

  if let Coordinate { x: 3.0, y } = coordinate {
    println!("(3, {})", y);
  } else {
    println!("x != three");
  }
}
```

We can also perform pattern matching using the match construct.

```rust
fn main() {
  let coordinate = Coordinate { x: 3.0, y: 5.0 }

  match coordinate {
    Coordinate { x: 3.0, y } => println!("(3, {})", y);
    _ => println!("x != three");
  }
}
```

Alternatively, this code also compiles:

```rust
fn main() {
  let coordinate = Coordinate { x: 3.0, y: 5.0 }

  match coordinate {
    Coordinate { x: 3.0, y } => println!("(3, {})", y);
    Coordinate { .. } => println!("x != three");
  }
}
```

`..` means ignore the (remaining) properties inside the Coordinate struct.


## Traits

Traits are like type classes in Haskell, or interfaces in Java. Say that we have a struct, Number which looks like this:

```rust
struct Number {
  value: isize,
  prime: bool
}
```

We could define a trait Parity that contains a function is_even. If we implement Parity for Number, we need to define the trait’s functions.

```rust
trait Parity {
  fn is_even(self) -> bool
}

impl Parity for Number {
  fn is_even(self) -> bool {
    self.value % 2 == 0
  }
}
```

We can also implement traits for foreign types as well!

```rust
// Using our struct for foreign type
impl Parity for i32 {
  fn is_even(self) -> bool {
    self % 2 == 0
  }
}

// Using foriegn trait for our struct
impl std::ops:Neg for Number {
  type Output = Number;

  fn neg(self) -> Self::Output {
    Number {
      value: -self.value
      ..self
    }
  }
}
```

Foreign traits cannot be defined for foreign structs

```rust
// * WILL NOT COMPILE
impl<T> std::ops::Neg for Vec<T> {
  type Output = isize;

  fn neg(self) -> Self::Output {
    -self.len()
  }
}
```


## Macros

Macros are a part of meta-programming. Marcos can be considered as little programs that other programs can use. All macros end with ! and can be defined as either of the following:

```rust
macro_name!()
macro_name!{}
macro_name![]
```

`println!` is a macro that uses `std::io` to write to the console.

`vec![]` defines a vector, an array like structure


```rust
fn main() {
  let vec1 = vec![1,2,3];

  for number in vec1 {
    println!("{number}");
  }
}
```

`panic!` is a macro that terminates a program Thread with an error message. `panic!` is one of the only places code can crash.


## Enums

Enums are types that are defined in an enclosure. The following example is coupled with Generics. Option is also defined in the standard library.

```rust
enum Option<T> {
  None,
  Some(T)
}

impl Option<T> {
  unwrap() -> T {
    match self {
      Self::None -> panic!("unwrap called on an Option None"),
      Self::Some -> T,
    }
  }
}
```


## The Result enum

Rust provides the enum `Result`.

```rust
enum Result<T, E> {
  Ok(T),
  Err(E)
}
```

When a function returns a result, we can safely handle it.

```rust
fn main() {
  {
    let result = do_something(); // returns result

    match result {
      Ok(data) => proceed(data),
      Err(error) => panic!("There has been an error!"),
    }

    // continue program execution
  }
}
```

The reason I have used this code within a scope block is if we wish to propagate the error up somewhere, we could replace the code with:

```rust
fn main() {
  {
    let result = do_something(); // returns result

    match result {
      Ok(data) => proceed(data),
      Err(error) => return error,
    }

    // continue program execution
  }
}
```

There is a shorthand to do this operation:

```rust
fn main() {
  {
    let data = do_something()?; // returns result

    // work with data directly
  }
}
```

Now if result returns an `Ok(data)`, then the question mark will return the data object to us.

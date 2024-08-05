---
{"dg-publish":true,"permalink":"/basics-of-rust/"}
---

# Basics of Rust
#### 1. Introduction:
- Rust is a systems programming language focused on safety, speed, and concurrency.
- It aims to provide memory safety without using a garbage collector, and it achieves this through a system of ownership with a set of rules that the compiler checks at compile time.

#### 2. Basic Data Types:

- **Scalar Types:**
  - **Integers:** `i8`, `i16`, `i32`, `i64`, `i128`, `isize` (signed), `u8`, `u16`, `u32`, `u64`, `u128`, `usize` (unsigned).
  - **Floating-point numbers:** `f32`, `f64`.
  - **Booleans:** `bool` (either `true` or `false`).
  - **Characters:** `char` (Unicode scalar values).

- **Compound Types:**
  - **Tuples:** A fixed-size collection of values of different types.
    ```rust
    let tup: (i32, f64, u8) = (500, 6.4, 1);
    ```
  - **Arrays:** A fixed-size collection of values of the same type.
    ```rust
    let arr: [i32; 3] = [1, 2, 3];
    ```

#### 3. Functions:

- Functions are defined using the `fn` keyword.
- They can take parameters and return a value.
- The type of each parameter must be declared, and if the function returns a value, the return type must be specified after an arrow (`->`).

  ```rust
  fn add(x: i32, y: i32) -> i32 {
      x + y
  }
  ```

#### 4. Control Flow:

- **If Statements:**
  ```rust
  let number = 5;

  if number < 10 {
      println!("The number is less than 10.");
  } else {
      println!("The number is 10 or greater.");
  }
  ```

- **Loops:**
  - `loop` for an infinite loop.
  - `while` for a conditional loop.
  - `for` for iterating over a collection.
  
  ```rust
  // Infinite loop
  loop {
      println!("This will loop forever.");
  }

  // Conditional loop
  let mut counter = 0;
  while counter < 5 {
      println!("Counter: {}", counter);
      counter += 1;
  }

  // Iterating over a collection
  let arr = [10, 20, 30, 40, 50];
  for element in arr.iter() {
      println!("Value: {}", element);
  }
  ```

#### 5. Ownership:

- Rust's ownership system is a set of rules that governs how memory is managed.
- **Ownership Rules:**
  1. Each value in Rust has a variable that’s called its owner.
  2. There can only be one owner at a time.
  3. When the owner goes out of scope, the value will be dropped.

  ```rust
  {
      let s = String::from("hello"); // s is valid from this point forward

      // do stuff with s
  }                                   // this scope is now over, and s is no longer valid
  ```

#### 6. Borrowing and References:

- To allow multiple parts of  code to access data without transferring ownership, Rust has the concept of references and borrowing.
- References are created using the `&` symbol.
- Mutable references (`&mut`) allow modifying the borrowed value.

  ```rust
  fn main() {
      let s1 = String::from("hello");
      let len = calculate_length(&s1);  // Borrowing

      println!("The length of '{}' is {}.", s1, len);
  }

  fn calculate_length(s: &String) -> usize {
      s.len()
  }
  ```

#### 7. Structs and Enums:

- **Structs** are used to create custom data types.
  ```rust
  struct User {
      username: String,
      email: String,
      sign_in_count: u64,
      active: bool,
  }

  let user1 = User {
      username: String::from("someone@example.com"),
      email: String::from("someone@example.com"),
      sign_in_count: 1,
      active: true,
  };
  ```

- **Enums** are used to define a type by enumerating its possible variants.
  ```rust
  enum Message {
      Quit,
      Move { x: i32, y: i32 },
      Write(String),
      ChangeColor(i32, i32, i32),
  }

  let msg = Message::Move { x: 10, y: 20 };
  ```

#### 8. Error Handling:

- Rust uses the `Result` and `Option` enums for error handling and optional values.

  ```rust
  fn read_file(filename: &str) -> Result<String, io::Error> {
      let mut file = File::open(filename)?;
      let mut contents = String::new();
      file.read_to_string(&mut contents)?;
      Ok(contents)
  }
  ```

#### 9. Modules:

- Rust's module system is used to organize code into separate namespaces.

  ```rust
  mod front_of_house {
      pub mod hosting {
          pub fn add_to_waitlist() {}
      }
  }

  use crate::front_of_house::hosting;

  fn main() {
      hosting::add_to_waitlist();
  }
  ```

#### 10. Cargo:

- Cargo is Rust's build system and package manager. It handles building your code, downloading dependencies, and more.

  ```sh
  cargo new my_project
  cd my_project
  cargo build
  cargo run
  cargo test
  cargo doc --open
  ```

---

---
{"dg-publish":true,"permalink":"/basics-of-go/"}
---

# Basics of Go

### Key Features

- **Statically typed**: Ensures type safety and allows for efficient compilation.
- **Compiled language**: Compiles directly to machine code, resulting in fast executables.
- **Concurrency**: Native support with goroutines and channels, enabling efficient handling of concurrent tasks.
- **Garbage collection**: Automated memory management.
- **Standard library**: Rich set of built-in libraries for common tasks, including networking, cryptography, and web development.
- **Cross-platform**: Supports major operating systems, including Windows, macOS, and Linux.

### Getting Started

- **Installation**: Download from the official Go website (https://golang.org/dl/).
- **Hello World**:
  ```go
  package main

  import "fmt"

  func main() {
      fmt.Println("Hello, World!")
  }
  ```

#### Variables

- **Declaration and initialization**:
  ```go
  var x int = 10
  y := 20  // shorthand
  ```

#### Data Types

- **Basic types**:
  ```go
  var a int = 5
  var b float64 = 3.14
  var c string = "Hello"
  var d bool = true
  ```

#### Flow Control

- **If-else statements**:
  ```go
  if a > b {
      fmt.Println("a is greater than b")
  } else {
      fmt.Println("b is greater than or equal to a")
  }
  ```

#### Loops

- **For loop**:
  ```go
  for i := 0; i < 10; i++ {
      fmt.Println(i)
  }
  ```

- **Range loop**:
  ```go
  nums := []int{2, 4, 6, 8}
  for index, value := range nums {
      fmt.Println(index, value)
  }
  ```

#### Functions

- **Function definition and call**:
  ```go
  func add(x int, y int) int {
      return x + y
  }

  func main() {
      sum := add(5, 3)
      fmt.Println("Sum:", sum)
  }
  ```

#### Arrays and Slices

- **Arrays**:
  ```go
  var arr [5]int
  arr[0] = 1
  arr[1] = 2
  fmt.Println(arr)
  ```

- **Slices**:
  ```go
  s := []int{1, 2, 3, 4, 5}
  s = append(s, 6)
  fmt.Println(s)
  ```

#### Maps

- **Map creation and usage**:
  ```go
  m := make(map[string]int)
  m["a"] = 1
  m["b"] = 2
  fmt.Println(m["a"])
  ```

#### Structs

- **Defining and using structs**:
  ```go
  type Person struct {
      Name string
      Age  int
  }

  func main() {
      p := Person{Name: "Alice", Age: 30}
      fmt.Println(p.Name, p.Age)
  }
  ```

#### Concurrency

- **Goroutines**:
  ```go
  func sayHello() {
      fmt.Println("Hello")
  }

  func main() {
      go sayHello()
      time.Sleep(1 * time.Second)  // wait for the goroutine to finish
  }
  ```

- **Channels**:
  ```go
  func sum(a []int, c chan int) {
      total := 0
      for _, v := range a {
          total += v
      }
      c <- total
  }

  func main() {
      a := []int{1, 2, 3, 4, 5}
      c := make(chan int)
      go sum(a, c)
      result := <-c
      fmt.Println(result)
  }
  ```

#### File Handling

- **Reading from a file**:
  ```go
  import (
      "bufio"
      "fmt"
      "os"
  )

  func main() {
      file, err := os.Open("test.txt")
      if err != nil {
          fmt.Println(err)
          return
      }
      defer file.Close()

      scanner := bufio.NewScanner(file)
      for scanner.Scan() {
          fmt.Println(scanner.Text())
      }

      if err := scanner.Err(); err != nil {
          fmt.Println(err)
      }
  }
  ```

- **Writing to a file**:
  ```go
  import (
      "fmt"
      "os"
  )

  func main() {
      file, err := os.Create("test.txt")
      if err != nil {
          fmt.Println(err)
          return
      }
      defer file.Close()

      file.WriteString("Hello, Go!\n")
  }
  ```
  
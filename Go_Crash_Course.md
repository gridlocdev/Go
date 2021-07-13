# Introduction to _```Go```_

This file will contain some scattered notes that I took from watching Brad Traversy's tutorial on ```Go```.

Table of Contents:

- [Introduction to _```Go```_](#introduction-to-go)
  - [**00_prelude** - Prelude](#00_prelude---prelude)
    - [Introduction to Go](#introduction-to-go-1)
    - [Installing the Go compiler](#installing-the-go-compiler)
    - [Go-path](#go-path)
  - [**01_hello** - Hello World](#01_hello---hello-world)
    - [Main - Package](#main---package)
    - [fmt package](#fmt-package)
    - [Declaring a function](#declaring-a-function)
    - [Starting point for a Go program](#starting-point-for-a-go-program)
    - [Executing a Go program](#executing-a-go-program)
  - [**02_vars** - Variables](#02_vars---variables)
    - [List of data types](#list-of-data-types)
    - [Variable type declarations](#variable-type-declarations)
    - [Mutability](#mutability)
    - [Global Variable Scope](#global-variable-scope)
    - [Assignment](#assignment)
  - [**03_packages** - Packages](#03_packages---packages)
    - [Import Syntax](#import-syntax)
    - [Creating a Package](#creating-a-package)
    - [Including a custom package](#including-a-custom-package)
  - [**04_functions** - Functions](#04_functions---functions)
    - [Void return types](#void-return-types)
    - [Typed return types](#typed-return-types)
    - [Calling Functions](#calling-functions)
  - [**5_arrays_slices** - Arrays and Slices](#5_arrays_slices---arrays-and-slices)
    - [Array Syntax](#array-syntax)
    - [Slices syntax](#slices-syntax)
    - [Other array methods - Length and sub-section](#other-array-methods---length-and-sub-section)
  - [**06_conditionals** - Conditionals](#06_conditionals---conditionals)
    - [If](#if)
    - [And / Or](#and--or)
    - [Else if / Else](#else-if--else)
    - [Switch statement](#switch-statement)
  - [**07_loops** - Loops](#07_loops---loops)
    - [For loops - long and short methods](#for-loops---long-and-short-methods)
    - [FizzBuzz](#fizzbuzz)
  - [**08_maps** - Maps (Key Value Pairs)](#08_maps---maps-key-value-pairs)
    - [Declaring a map](#declaring-a-map)
    - [Create and Update](#create-and-update)
    - [Read](#read)
    - [Delete](#delete)
  - [**09_range** - Ranges](#09_range---ranges)
    - [Regular loops](#regular-loops)
    - [Range loops - with index](#range-loops---with-index)
    - [Range loops - without index](#range-loops---without-index)
    - [Ranges with Maps](#ranges-with-maps)

## **00_prelude** - Prelude

---

### Introduction to Go

The philosophy behind Go is that the language is simple and powerful, and people can pick it up easily between computers and projects. So, there are a few things to know before getting started.

### Installing the Go compiler

You can find this either on GoLang's website or via your operating system's Package Management system. As with most languages, the compiler must be installed before programs can be run.

### Go-path

All of the files and programs for Go live in the same place. This place is called your **Workspace**; otherwise known more specifically as the **GOPATH**

You can see where the Go default workspace is on your machine by typing:

```Bash
go env GOPATH
```

As an example, my Workspace directory in Ubuntu Linux is in ```/home/{{username}}/go``` by default. You can also change where this folder is by editing the Go configuration on your machine if you'd prefer it to be somewhere else.

---

## **01_hello** - Hello World

---

### Main - Package

The ```package main``` line signifies that this file can be executed.

```go
package main
```

The syntax "package" is like a namespace in C#. It's an identifier you add to a particular file to say how it should be referenced by both the Go runtime and other files you create.

---

### fmt package

The **fmt** package lets you do basic IO like println similar to how it it works in C. You import it like this:

```go
import (
    "fmt"
)
```

> Note: When multiple packages are present, Go does not use commas to delimit packages. Instead, each package should generally be on a new line. This also makes auto-additions easier in VSCode's IntelliSense auto-additions.

---

### Declaring a function

Functions are called with "func functionName() {}" like JavaScript

---

### Starting point for a Go program

The "```main```" function is the initial point that the program code starts to execute just like C# and other languages.

---

### Executing a Go program

To execute the go program, run ```go install```. The outputted executable file should now be in your GOPATH under the /bin folder

```bash
go install
```

---

## **02_vars** - Variables

---

### List of data types

```go
// MAIN TYPES
// string
// bool
// int
// int  int8  int16  int32  int64
// uint uint8 uint16 uint32 uint64 uintptr
// byte - alias for uint8
// rune - alias for int32
// float32 float64
// complex64 complex128
```

> **Note: uint - Un-signed Integer**
>
> - The "u" in uint stands for **unsigned**, meaning no "sign" can be on the number. This basically means the number can have no negative and can be assigned values 0 and up.

---

### Variable type declarations

In go, you can initialize a variable type in two ways:

- Specify the exact type
- Infer the type from what value you assign to it

```go
/* -- Creating a Variable -- */

// {With type}
var name string = "Aaron"
var age int32 = 37
const gender string = "Male" 
fmt.Println(name, age)

// Without type
var name_2 = "Aaron"
var age_2 = 37
const gender = "Male"
fmt.Println(name_2, age_2)
```

---

### Mutability

```var``` and ```const```

Just like JavaScript ES6, you can use both _var_ and _const_ to declare variable scope. _Var_ is mutable, and _const_ is immutable.

```go
var name = "John"
const gender = "Male"
```

---

### Global Variable Scope

You can have global variables in a Go codefile.

```go
package main

import "fmt"

var name = "John"

func main() {
    fmt.Println("Hello, " + name + "!")
}
```

> Note: The shorthand syntax ":=" for assigning to a mutable variable using var cannot be used outside a function, which means it cannot be used to assign values to global variables.

---

### Assignment

For ```var```, in addition to the regular syntax there is a shorthand syntax for non-global variables.

```go
// Regular "var" syntax
var name = "Bob"

// Shorthand in-function syntax
name := "Bob"
```

You can also assign muliple values on a single line using the shorthand syntax.

```go
name, email := "Bob", "Email@example.com"
```

---

## **03_packages** - Packages

---

### Import Syntax

The default package syntax looks like this, with each package included on a new line:

```go
import (
    "fmt"
    "math"
)
```

This also makes it easier for IntelliSense to add new packages similar to how it does in Angular.

---

### Creating a Package

To create a package, initialize the file with the name you'd like to set as the package name. (It's like a namespace in C#.)

```go
/* File: strutil/reverse.go */ 

package strutil

/* 

Code goes here 

*/
```

---

### Including a custom package

In go, you import local packages through the path. So, a package in the directory ~/go/src/github.com/gridlocdev/Hello-World/03_packages/strutil would be imported by path.

All of the package titles (```package ...```) in files included in that folder path are now usable in the file that contains the import statement.

Example:

```go
package main

import (
    "fmt"
    "math"
    "github.com/gridlocdev/Go-Crash-Course/03_packages/strutil"
)

func main() {
    // In this case, the strutil.reverse() method reverses the inputted string.
    fmt.Println(strutil.reverse("Hello World!"))
}
```

---

## **04_functions** - Functions

Functions are very simple and similar to other languages. Here is the syntax for Go.

---

### Void return types

- The return type is void if no return type is specified

```go
func doSomething() {
    // code here
}
```

---

### Typed return types

- The return type is specified after the parameter list, like TypeScript does.

```go
func addNumbers(num1 int, num2 int) int {
    return num1 + num2
}
```

---

### Calling Functions

- To call a function in another function, it's done the usual way.

```go
func addNumbers(num1 int, num2 int) int {
    return num1 + num2
}

func main() {
    fmt.Println(addNumbers(3, 4))
}
```

---

## **5_arrays_slices** - Arrays and Slices

---

### Array Syntax

> Arrays are fixed-size, you initialize a number of available spaces and have that to work with.

- Declare + Assign separately

```go
// Declaring an array of size 2 with strings in it
var fruits [2]string

// Initializing the values of that array
fruits[0] = "Apple"
fruits[0] = "Orange"
```

- Declaration + assign together

```go
fruits := [2]string{"Apple","Orange"}
```

---

### Slices syntax

> Slices are variable-size, the length can be increased and decreased as needed.

```go
fruitSlice := []string{"Banana","Grape"}
```

---

### Other array methods - Length and sub-section

- Length - ```len()```

```go
array := []string{"One","Two","Three"}
fmt.Println(len(array)) /* Outputs "3" */
```

- Range - ```[x:y]```

```go
array := []string{"One","Two","Three"}
fmt.Println(array[1:3]) /* Outputs "[Two Three]" */
```

> Note: In the range syntax ```[1:3]``` means the section begins including the value at index 1, but stops before the index 3.
> [x:3] x = the index to start grabbing values from E.g. ```fruits[1]```
> [1:x] x = the position of the array to stop grabbing values on, meaning it is not included.

---

## **06_conditionals** - Conditionals

---

### If

In Go conditionals, you do not need to include () around your clause.

```go
x := 1
y := 2

if x < y {
    fmt.Printf(%d is less than %d, x, y)
}
```

> Note: The ```Printf()``` function is used to print _formatted_ output, meaning it is used when you need to translate text, numbers, or other values before you output the result. There are a number of placeholders to use and each serves a particular purpose or data type which can be found at GoLang's documentation at [GoLang - fmt package documentation link](https://golang.org/pkg/fmt/)

---

### And / Or

The syntax is the same as JavaScript, using either && for "and", and || for "or".

```go
// AND
number := 15

if number > 10 && number < 25 {
  fmt.Println("The number is between 10 and 25!")
} 

// OR
name := "Bob"

if name == "Bob" || name == "John" {
  fmt.Println("The name is either Bob or John")
}

```

---

### Else if / Else

It's the same syntax as JavaScript, with If, Else if, and Else

```go
var color string = "Red"

// If block with Else if / Else
if color == "Red" {
  fmt.Println("Color is Red")
} else if color == "Blue" {
  fmt.Println("Color is Blue")
} else {
  fmt.Println("Color is not Blue or Red")
}
```

---

### Switch statement

```go
var color string = "Red"

// Switch
switch color {
case "Red":
  fmt.Println("Color is Red")
case "Blue":
  fmt.Println("Color is Blue")
default:
  fmt.Println("Color is not Blue or Red")
}
```

---

## **07_loops** - Loops

---

### For loops - long and short methods

```go
// Long method (For when your variable isn't loop scoped)
i := 1
for i <= 10 {
  fmt.Println(i)
  i++
}

// Short method
for i := 1; i <= 10; i++ {
  fmt.Printf("Number: %d", i)
}
```

### FizzBuzz

```go
// FizzBuzz
/*
  Find all the numbers between 0 and 100 that are divisible by 3 and 5.
  If the number is divisible by 3, print out "Fizz"
  If the number is divisible by 5, print out "Buzz"
  If the number is divisible by both 3 and 5, print out "FizzBuzz"
*/
for i := 1; i <= 100; i++ {
  if i%15 == 0 {
    fmt.Printf("%d: FizzBuzz\n", i)
  } else if i%3 == 0 {
    fmt.Printf("%d: Fizz\n", i)
  } else if i%5 == 0 {
    fmt.Printf("%d: Buzz\n", i)
  } else {
    fmt.Printf("%d:\n", i)
  }
}
```

> Note: The **modulus** operator **```%```** represents a _remainder_ in division.

---

## **08_maps** - Maps (Key Value Pairs)

---

Maps are another name for key-value pairs.

### Declaring a map

Declaring a map means creating an empty instance.

```go
// Declaring an empty map
emails := make(map[string]string)
```

> The ```make()``` command initializes and assigns memory for the set of key-value pairs based on the data structure you assign in the "map" parameters.

---

### Create and Update

In Go, both Create and Update operations to an item in a map use the same syntax.

```go
// Declaring an empty map
emails := make(map[string]string)

// Creating individual new key-values to that map
emails["Bob"] = "bob@gmail.com"
emails["Sharon"] = "sharon@gmail.com"
emails["Mike"] = "mike@gmail.com"

// Updating a single key-value in that map
emails["Bob"] = "bobby@gmail.com"
```

Shorter syntax for creating a map with initialized values:

```go
// Declare map and add key-value pairs
emails := map[string]string{
  "Bob":    "bob@gmail.com",
  "Sharon": "sharon@gmail.com",
  "Mike":   "mike@gmail.com",
}
```

> Note: The short syntax does not use the ```make()``` function. Instead, the Go compiler infers values to be made from what is placed into the {} after the initialization keywords.

---

### Read

```go
// Declare map and add key-value pairs
emails := map[string]string{
  "Bob":    "bob@gmail.com",
  "Sharon": "sharon@gmail.com",
  "Mike":   "mike@gmail.com",
}

// Read an item from a map (Printed to console)
fmt.Println(emails["Bob"])
```

---

### Delete

To delete an item from a map, you use the ```delete()``` function.

```go
// Declare map and add key-value pairs
emails := map[string]string{
  "Bob":    "bob@gmail.com",
  "Sharon": "sharon@gmail.com",
  "Mike":   "mike@gmail.com",
}

// Delete a key-value pair from the map
delete(emails["Bob"])
```

---

## **09_range** - Ranges

A range is used to loop through a set of values in an ordered list.

These are used not as its own data type like Array or Slice, but rather part of loops to assist with easier enumeration.

### Regular loops

For reference, here is how a regular loop looks that does not use ranges.

```go
ids := []int{33, 25, 34, 216, 1, 12}

// Regular way of looping using three parameters
for i := 0; i < len(ids); i++ {
  fmt.Println(ids[i])
}
```

### Range loops - with index

When you would like to loop through a data structure, it persists an _index_ to establish where to look and take things from.

```go
ids := []int{33, 25, 34, 216, 1, 12}

// Range method with index
for i, id := range ids {
  fmt.Printf("%d - ID: %d\n", i, id)
}
```

### Range loops - without index

In Go, this is the equivalent of a ```foreach``` loop from other languages. The main difference is the easier definition of multiple variables inside a single loop.

These multiple variable definitions allow you to easily use the _index_ and _value_, similar to how a foreach loop would.

> The way that a for loop specifies no index is to use a placeholder "**```_```**" instead of a named index variable.

```go
ids := []int{33, 25, 34, 216, 1, 12}

// Range method without index
for _, id := range ids {
  fmt.Printf("ID: %d\n", id)
}

// Add together the array of ids and output the sum
sum := 0
for _, id := range ids {
  sum += id
  fmt.Printf("Total: %d | Added: %d\n", sum, id)
}
```

> Note: The character "**```_```**" is a reserved variable name that represents a an unused parameter. This can act as an empty placeholder so that the next argument in the for loop's parameter list is able to be assigned.

### Ranges with Maps

The ```range``` operator allows for you to translate parameters into indexes in the various data structures available, such as arrays and maps (and some others that I have not learned yet)

This is an example of a loop through a map.

```go
// Range with map
emails := map[string]string{
  "Bob":    "bob@gmail.com",
  "Sharon": "sharon@gmail.com",
  "Mike":   "mike@gmail.com",
}
for name, email := range emails {
  fmt.Printf("Key: %s | Value: %s\n", name, email)
}
for name := range emails {
  fmt.Printf("Name: %s\n", name)
}
```

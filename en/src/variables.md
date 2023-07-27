# Variables

### Binding and mutability

1. 🌟 A variable can be used only if it has been initialized.

```rust,editable
fn main() {
    let x: i32 = 5; // Uninitialized but used, ERROR !
    let y: i32; // Uninitialized but also unused, only a Warning !

    assert_eq!(x, 5);
    println!("Success!");
}
```

---

2. 🌟 Use `mut` to mark a variable as mutable.

```rust,editable

/**
 *  Declare default variable is immutable => like 'const' but have some different
 *
 * It relate to Compile-time constants, compile-time evaluable functions, and raw pointers.
 *  ### Compile-time constants
 * - Use a common variable many time => copy and copy over => complicated and inconvenient
 *          - > So Rust provide alternative avoid duplicated: Ex:
 *              const THING:u32 = 0xABAD1DEA;  => let foo = 123 + THING;
 * - Constants must be explicitly typed => Not like 'let' , ex: can not assign File to 'const'
 * - The only lifetime allowed in a constant is 'static
 * - Note: Constants, like statics, should always be in `SCREAMING_SNAKE_CASE`
 * %%% Lifetime
 * -A lifetime is a construct of the compiler (or more specifically, its borrow checker) uses to ensure all borrows are valid.
 * ### Compile-time evaluable functions
 *  const fn
 - #### Other Use
    The const keyword is also used in raw pointers in combination with mut, as seen in *const T and *mut T
 * Ref: https://doc.rust-lang.org/std/primitive.pointer.html
*/
fn main() {
    let mut x = 1;
    x += 2;

    assert_eq!(x, 3);
    println!("Success!");
}
```

### Scope

A scope is the range within the program for which the item is valid.

3. 🌟

```rust,editable

// It related to scope program => Y if not declare out of block code => It can not use
fn main() {
    let x: i32 = 10;
    let y: i32 = 5;
    {

        println!("The value of x is {} and value of y is {}", x, y);
    }
    println!("The value of x is {} and value of y is {}", x, y);
}
```

4. 🌟🌟

```rust,editable

fn main() {
    let x=define_x();
    println!("{}, world", x);
}
// return function String
fn define_x()->String {
    String::from("hello")

}
```

### Shadowing

5. 🌟🌟

```rust,editable

// Only modify `assert_eq!` to make the `println!` work(print `42` in terminal)
// Exercise relate to scope and shadowed variable => decare a new variable with the same name with a previous variable =>shadowed
fn main() {
    let x: i32 = 5;
    {

        let x = 12;
        assert_eq!(x, 12);
    }

    assert_eq!(x, 5);

    let x = 42;
    println!("{}", x); // Prints "42".
}
```

6. 🌟🌟

```rust,editable

// Remove a line in the code to make it compile
fn main() {
    //declare a variable x
    let mut x: i32 = 1;
    x = 7; // re assigned it => 7
    // Shadowing and re-binding
    let mut x = x; // shadowing but it x = 7 =>> remmber shadowing and re-binding also rebuild
    x += 3; // x =10


    let y = 4;
    // Shadowing
    let y = "I can also be bound to text!";

    println!("Success!");
}
```

### Unused variables

7. Fix the warning below with :

- 🌟 Only one solution
- 🌟🌟 Two distinct solutions

> Note: none of the solutions is to remove the line `let x = 1`

```rust,editable
// or we can add attribute
#[allow(unused_variables)]
fn main() {
    let _x = 1;
}

// Warning: unused variable: `x`
```

### Destructuring

8. 🌟🌟 We can use a pattern with `let` to destructure a tuple to separate variables.

> Tips: you can use Shadowing or Mutability

```rust,editable

// Fix the error below with least amount of modification
fn main() {
    let  (mut x, mut y) = (1, 2);
    x += 2;

    assert_eq!(x, 3);
    assert_eq!(y, 2);

    println!("Success!");
}
```

### Destructuring assignments

Introduced in Rust 1.59: You can now use tuple, slice, and struct patterns as the left-hand side of an assignment.

9. 🌟🌟

> Note: the feature `Destructuring assignments` need 1.59 or higher Rust version

```rust,editable

fn main() {
    let (x, y);
    (x,..) = (3, 4); // x = 3 => destructoring
    [.., y] = [1, 2];// y =2
    // Fill the blank to make the code work
    assert_eq!([x,y], [3,2]);

    println!("Success!");
}
```

> You can find the solutions [here](https://github.com/sunface/rust-by-practice)(under the solutions path), but only use it when you need it

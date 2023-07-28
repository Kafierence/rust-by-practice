# Statements and Expressions

### Examples

```rust,editable

// let allow bind a value to a variable
//
fn main() {
    let x = 5u32;

    let y = {
        let x_squared = x * x; // 25
        let x_cube = x_squared * x; // 25x5 = 125

        // This expression will be assigned to `y`
        x_cube + x_squared + x //155
    };

    let z = {
        // The semicolon suppresses this expression and `()` is assigned to `z`
        2 * x;
    };

    println!("x is {:?}", 5);
    println!("y is {:?}", 155);
    println!("z is {:?}", 10);
}

```

### Exercises

1. 🌟🌟

```rust,editable
// Make it work with two ways
fn main() {
    let v = {
        let mut x = 1;
        x + 2 // return not expression -> number
    };

    assert_eq!(v, 3);

    println!("Success!");
}

```

2. 🌟

```rust,editable
// let statement is use to introduce new variable , you can not assign it value tuple existing
fn main() {
    let v = 3;

    assert!(v == 3);

    println!("Success!");
}
/**
 *  Or build something like this
 * let v = (1, 2, 3);
 * assert!(v == (1, 2, 3));
*/

```

3. 🌟

```rust,editable

fn main() {
    let s = sum(1 , 2);
    assert_eq!(s, 3);

    println!("Success!");
}

fn sum(x: i32, y: i32) -> i32 {
    x + y
}
```

> You can find the solutions [here](https://github.com/sunface/rust-by-practice)(under the solutions path), but only use it when you need it

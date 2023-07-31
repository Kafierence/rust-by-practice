# Ownership

1. 🌟🌟

```rust,editable

fn main() {
    // Use as many approaches as you can to make it work
    let x = String::from("hello, world");
    let y = &x;
    println!("{},{}", x, y);
}
```

2. 🌟🌟

```rust,editable
// Don't modify code in main!
/**
 *  The firsthing will talk about ownership in rust:
 *  it is fundamental concept how memory is managed and how data is shared between different parts of the program.
 *
*/
fn main() {
    let s1 = String::from("hello, world");
    let s2 = take_ownership(s1);

    println!("{}", s2);
}

// Only modify the code below!
fn take_ownership(s: String) -> String { // return value
    println!("{}", s);
    s
}
```

3. 🌟🌟

```rust,editable
 // convert String into bytes [number ...] =>Vec<u8>
fn main() {
    let s = give_ownership();
    println!("{:?}", s);
}

// Only modify the code below!
fn give_ownership() -> Vec<u8> {
    let s = String::from("hello, world");
    // Convert String to Vec
    let _s = s.into_bytes();
    _s
}

```

4. 🌟🌟

```rust,editable
// Fix the error without removing code line
//Pass the reference
//  this error relate to browsering and ownership
// It relate to Data races Prevention => Ensure that data races
// When a value paased as an argument to a function , it is moved from the original to a new place => after a move , the original variable can no longer be used => preventing any accidental use of an invalidated references

fn main() {
    let s: String = String::from("hello, world");

    print_str(&s);

    println!("{}", s);
}

fn print_str(s: &String) {
    println!("{}", s);
}

```

5. 🌟🌟

```rust,editable


// Don't use clone ,use copy instead
/**
 *  clone () method : create a shallow copy of the value => should use for type contain reference , complex data ownership ...
 *  copy () method: allows vallue to be duplicated using a simple bitwise copy instead of a deep copy. => should use for the non-refrence and string...
 *
*/
fn main() {
    let x = (1, 2, (), "hello".to_string());
    let y = (x.0, x.1, x.2, x.3.clone());
    println!("{:?}, {:?}", x, y);
}

```

#### Mutability

Mutability can be changed when ownership is transferred.

6. 🌟

```rust,editable

fn main() {
    let s = String::from("hello, ");

    // Modify this line only !
    let mut s1 = s;

    s1.push_str("world");

    println!("Success!");
}
```

7. 🌟🌟🌟

```rust,editable

fn main() {
    let x = Box::new(5);

    let ...      // Implement this line, dont change other lines!

    *y = 4;

    assert_eq!(*x, 5);

    println!("Success!");
}
```

### Partial move

Within the destructuring of a single variable, both by-move and by-reference pattern bindings can be used at the same time. Doing this will result in a partial move of the variable, which means that parts of the variable will be moved while other parts stay. In such a case, the parent variable cannot be used afterwards as a whole, however the parts that are only referenced (and not moved) can still be used.

#### Example

```rust,editable

fn main() {
    #[derive(Debug)]
    struct Person {
        name: String,
        age: Box<u8>,
    }

    let person = Person {
        name: String::from("Alice"),
        age: Box::new(20),
    };

    // `name` is moved out of person, but `age` is referenced
    let Person { name, ref age } = person;

    println!("The person's age is {}", age);

    println!("The person's name is {}", name);

    // Error! borrow of partially moved value: `person` partial move occurs
    //println!("The person struct is {:?}", person);

    // `person` cannot be used but `person.age` can be used as it is not moved
    println!("The person's age from person struct is {}", person.age);
}
```

#### Exercises

8. 🌟

```rust,editable

fn main() {
   let t = (String::from("hello"), String::from("world"));

   let _s = t.0;

   // Modify this line only, don't use `_s`
   println!("{:?}", t.1);
}
```

9. 🌟🌟

```rust,editable

fn main() {
    let t = (String::from("hello"), String::from("world"));

    // Fill the blanks
    let (s1, s2) = t.clone();

    println!("{:?}, {:?}, {:?}", s1, s2, t); // -> "hello", "world", ("hello", "world")
}
```

> You can find the solutions [here](https://github.com/sunface/rust-by-practice/blob/master/solutions/ownership/ownership.md)(under the solutions path), but only use it when you need it

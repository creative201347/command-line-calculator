







## [Command Line Arguments](https://www.youtube.com/watch?v=MsocPEZBd-M&ab_channel=freeCodeCamp.org)

The Rust standard library comes with an `env` module, which allows access to the command line arguments passed when calling the program. Returns the arguments that this program was started with (normally passed via the command line).
The first element is traditionally the path of the executable, but it can be set to arbitrary text, and might not even exist. This means this property should not be relied upon for security purposes.

```
use std::env::args;

fn main() {
    let mut args = args();

    let first = args.nth(1).unwrap();
    let operator = args.nth(0).unwrap().chars().next().unwrap();
    let second = args.nth(0).unwrap();
```

The first and second variables are `strings`, and you need to parse them into `numbers`. The String struct implements the parse method, which takes a type annotation, and returns a Result containing the parsed value.
```
let first_number = first.parse::<f32>().unwrap();
let second_number = second.parse::<f32>().unwrap();
```


The `match` expression works similarly to a `switch` statement in other languages. The match expression takes a value, and a list of arms. Each arm is a pattern and block. The pattern is a value to match against, and the block is the code to execute if the pattern matches. The `_` pattern is a wildcard, acting like an `else` clause.
```
fn operate(operator: char, first_number: f32, second_number: f32) -> f32 {
    match operator {
        '+' => first_number + second_number,
        '-' => first_number - second_number,
        '*' | 'x' | 'X' => first_number * second_number,
        '/' => first_number / second_number,
        _ => panic!("Invalid operator used!!"),
    }
}
```

The `--release` flag tells Cargo to build the binary in release mode. This will reduce the size of the binary, and will also remove any debugging information.
The binary is built in the `target/release` directory. 
```
cargo build --release

./target/release/day2 1 + 10
cargo run -- 10 - 2
```


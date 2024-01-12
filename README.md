# Wombat
Wombat is a young, simple, and effective programming language developed for educational purposes.

# Official syntax of the Wombat programming language, Bran the mascot.
This README file contains the official syntax and grammar of Wombat as this is the first step of every programming language.

## Wombats simple conditions :)

```system.print()``` outputs a given input into the terminal.
* {n} => integers.
* {s} => strings, enums, or structs.
* {e} => errors.

E.g. ```system.print("Hello, {s}", "World!");```

The ```pack()``` function is a built-in function given to compute a certain expression.
For example in ```system.print("What? {n}", pack(1 + 2));``` the pack(1 +2) will return 3. <br />
You can say Wombat relies on the programmer to compute anything :)

Wombat adapts to the camelCase grammar.

## Variables

Wombat defaults all variables to be mutable.
You can create an immutable variable by using ```var!``` instead of ```var```.

## Types
Documentation will be added in the future.

### int
Usage: ```var x: int = 5;```.
The above line defines a mutable integer value named x with the value of 5.

### float
Usage: ```var! pi: float = 3.14```.
The above line defines an immutable float constant pi. (Yes, the famous one...).

### string
Usage: ```var! hello_wombat: string = "Hello, Wombat!";```
The above line defines a string constant named hello_wombat with the value of "Hello, Wombat!".

### ch
Usage: ```var letter: ch = "w";```
The above line defines a mutable char named letter with the value of "w".

### structs
Struct names and Fields must be capitalized.
Usage: 
```
create Dog :: Struct {
    Name: string,
    Age: int
};

fnc newAnimal(name: string, age: int) >> Animal {
    return Animal { Name: name, Age: age };
}

var darky: Animal = Animal {Name: "Darky", Age: 5};
var lucy: Animal = newAnimal("Lucy", 7); 
```

### arrays
Usage: ```var peopleNames: string[3] = ["Hello", "Happy", "Bran"];```

### enums
Enum names and variants must be capitalized.
Usage: 
```
Ip :: enum {
    IpV4(string),
    IpV6(string),
}
var! localhost: Ip->IpV4 = Ip->IpV4("127.0.0.1");
```

### funny
Wombat takes this feature (With credit of course) from languages like Rust and Zig. 
funny is a special built-in optional type in Wombat. It wraps another type but it can hold an error as well.
under the hood funny is implemented as follows:
```
funny :: enum {
    FunnyInner(inside_it),
    FunnyError(error)    
}
```
Usage will be through if statements, try catches, and simple variable declarations. <br />
E.g. ```var maybeOk: funny(int) = Wrapper(5);  funny initialization.```

## Control flow
Wombats control flow aims to be as simple as possible and efficient at the same time.

### while
```
var i: int = 0;
while true: {
    system.print("{n} - Hello, wombat!", i);
    i += 1;
}
```

### for
```
for (i: int = 0, i <= 10, i += 2) {
    system.print("Jumping! {n}", i);
}
```

### if statements.
Wombat doesn't support elif statements.
Usage:
```
var x: int = 5;
if x != 5 -> {
    system.print("X is not 5!);
} else {
    system.print("X is 5!");
}
```

A ```funny``` if statement snippet using funny's simple capabilities.
```
if someFunc(x) -> |success| {
    system.print("A funny success!");
} else -> |error| {
    system.print("{e} happened", error)
}
```
The snippet above computes ```someFunc(x)``` and if the funny inner value is not an error the inner value will be dropped into ```success```, otherwise the ```error``` will hold the inner error of someFunc.

### try catch.
```
try {
    var a: int = 10;
    var b: int = 0;
    system.print("a divided by b is: {n}", pack(a / b));
}
catch |error| {
    system.print("{e} was caught!", error);
}
```

## Functions

Simple syntax: 
```
fnc name(args: types) >> returnType {
    // The functions` work.
}
```

Examples:
```
fnc greet_user(user_name: string) >> void {
    system.print("Hello, {s}", user_name);
}

fnc divide(a: int, b: int) >> funny(int) {
    return a / b;
}
```

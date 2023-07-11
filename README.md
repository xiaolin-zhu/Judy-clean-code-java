# clean-code-java

## Table of Contents
  1. [Introduction](#introduction)
  2. [Meaningful Names](#meaningful-names)
  3. [Functions](#functions)

## Introduction
Software engineering principles, from Robert C. Martin's book
[*Clean Code*](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882),
adapted for Java.

## **Meaningful Names**
### Use Intention-Revealing Names
The name of a variable, function or class, should answer all the big questions. It should tell you why it exists, what it does, and how is used. If a name requires a comment, then the name does not reveals its intent.

**Bad:**
```java
List<int[]> list1 = new ArrayList<int[]>();
```

**Good:**
```java
List<int[]> flaggedCells = new ArrayList<int[]>();
```
**[⬆ back to top](#table-of-contents)**

### Avoid Disinformation
Programmers must avoid leaving false clues that obscure the meaning of code. We should avoid words whose entrenched meaning vary from our intended meaning.

**Bad:**
```java
String accountList = "Jack,Tom,Tony";
```

**Good:**
```java
String accounts = "Jack,Tom,Tony";
```
**[⬆ back to top](#table-of-contents)**

### Make Meaningful Distinctions
Programmers create problems for themselves when they write code solely to satisfy a compiler or interpreter.Example, you create the variable `klass` because the name `class` was used for something else.

**Bad:**
```java
public static void copyChars(char a1[], char a2[]) {
  for (int i = 0; i < a1.length; i++) {
    a2[i] = a1[i];
  }
}
```

**Good:**
```java
public static void copyChars(char source[], char destination[]) {
  for (int i = 0; i < source.length; i++) {
    destination[i] = source[i];
  }
}
```
**[⬆ back to top](#table-of-contents)**

### Use Pronounceable Names

**Bad:**
```java
private Date genymdhms;
```

**Good:**
```java
private Date generationTimestamp;
```
**[⬆ back to top](#table-of-contents)**

### Use Searchable Names
Single-letter names and numeric constants have a particular problem in that they are not easy to locate across a body of text.

**Bad:**
```java
private String a;
```

**Good:**
```java
private String userName;
```
**[⬆ back to top](#table-of-contents)**

### Avoid Encoding
We have enough encodings to deal with without adding more to our burden.

**Bad:**
```java
private String m_dsc;
```

**Good:**
```java
private String description;
```
**[⬆ back to top](#table-of-contents)**

### Avoid Mental Mapping
Readers shouldn't have to mentally translate your names into other names they already know.

One difference between a smart programmer and a professional programmer is that the professional understands that clarity is king. Professionals use their powers for good and write code that others can understand.

**[⬆ back to top](#table-of-contents)**

### Class Names
Classes and objects should have noun or noun phrase names like `Customer`, `WikiPage`, `Account`, and `AddressParser`. Avoid words like `Manager`,`Processor`,`Data`, or `Info` in the name of a class. A class name should not be a verb.

**[⬆ back to top](#table-of-contents)**

### Method Names
Methods should have verb or verb phrase names like `postPayment`, `deletePage` or `save`. Accessors, mutators, and predicates should be named for their value and prefixed with get, set, and is according to the javabean standard.

**[⬆ back to top](#table-of-contents)**

### Don't Be Cute

**Bad Name:**
```java
holyHandGranade
```

**Good Name:**
```java
deleteItems
```

**[⬆ back to top](#table-of-contents)**

### Pick one word per concept
Pick one word for one abstract concept and stick with it. For instance, it’s confusing to have fetch, retrieve, and get as equivalent methods of different classes.

**[⬆ back to top](#table-of-contents)**

### Don’t Pun
Avoid using the same word for two purposes. Using the same term for two different ideas is essentially a pun.

Example: in a class use `add` for create a new value by adding or concatenating two existing values and in another class use `add` for put a simple parameter in a collection, it's a better options use a name like  `insert` or `append` instead.

**[⬆ back to top](#table-of-contents)**

### Use Solution Domain Names
Remember that the people who read your code will be programmers. So go ahead and use computer science (CS) terms, algorithm names, pattern names, math terms, and so forth.

**[⬆ back to top](#table-of-contents)**

### Use Problem Domain Names
When there is no “programmer-eese” for what you’re doing, use the name from the problem domain. At least the programmer who maintains your code can ask a domain expert what it means.

**[⬆ back to top](#table-of-contents)**

### Add Meaningful context
There are a few names which are meaningful in and of themselves—most are not. Instead, you need to place names in context for your reader by enclosing them in well-named classes, functions, or namespaces.

**Bad Name:**
```java
state
```

**Good Name:**
```java
addrState
```

**[⬆ back to top](#table-of-contents)**

### Don’t Add Gratuitous Context
In an imaginary application called “Gas Station Deluxe,” it is a bad idea to prefix every class with GSD. Example: `GSDAccountAddress`

Shorter names are generally better than longer ones, so long as they are clear. Add no more context to a name than is necessary.

**[⬆ back to top](#table-of-contents)**

## Functions
### Small
The first rule of functions is that they should be small. The second rule of functions is that they should be smaller than that.

#### Blocks and Indenting

This implies that the blocks within `if` statements, `else` statements, `while` statements, and so on should be one line long. Probably that line should be a function call. Not only does this keep the enclosing function small, but also adds documentary value because the function called within the block can have a nicely descriptive name.

This also implies that functions should not be large enough to hold nested structures. Therefore, the indent level of a function should not be greater than one or two. This, of course, makes the functions easy to read and understand.

**[⬆ back to top](#table-of-contents)**

### Do One Thing
**FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY.**

**Bad:**
```java
public void emailClients(List<Client> clients) {
    for (Client client : clients) {
        Client clientRecord = repository.findOne(client.getId());
        if (clientRecord.isActive()){
            email(client);
        }
    }
}
```

**Good:**
```java
public void emailClients(List<Client> clients) {
    for (Client client : clients) {
        if (isActiveClient(client)) {
            email(client);
        }
    }
}

private boolean isActiveClient(Client client) {
    Client clientRecord = repository.findOne(client.getId());
    return clientRecord.isActive();
}
```

**[⬆ back to top](#table-of-contents)**

### One Level of Abstraction per Function
In order to make sure our functions are doing "one thing", we need to make sure that the statements within our function are all at the same level of abstraction.

#### Reading Code from Top to Bottom: The Stepdown Rule

We want the code to read like a top-down narrative. 5 We want every function to be followed by those at the next level of abstraction so that we can read the program, descending one level of abstraction at a time as we read down the list of functions.

**[⬆ back to top](#table-of-contents)**

### Switch Statements
It’s hard to make a small switch statement. 6 Even a switch statement with only two cases is larger than I’d like a single block or function to be. It’s also hard to make a switch statement that does one thing. By their nature, switch statements always do N things. Unfortunately we can’t always avoid switch statements, but we can make sure that each switch statement is buried in a low-level class and is never repeated. We do this, of course, with polymorphism.

**[⬆ back to top](#table-of-contents)**

### Use Descriptive Names

**Bad:**
```java
private void addToDate(Date date, int month){
    //..
}

Date date = new Date();

// It's hard to to tell from the method name what is added
addToDate(date, 1);
```

**Good:**
```java
private void addMonthToDate(Date date, int month){
    //..
}

Date date = new Date();
addMonthToDate(1, date);
```

**[⬆ back to top](#table-of-contents)**

### Function arguments
The ideal number of arguments for a function is zero (niladic). Next comes one (monadic), followed closely by two (dyadic). Three arguments (triadic) should be avoided where possible. More than three (polyadic) requires very special justification—and then shouldn’t be used anyway.

Arguments are even harder from a testing point of view. Imagine the difficulty of writing all the test cases to ensure that all the various combinations of arguments work properly. If there are no arguments, this is trivial. If there’s one argument, it’s not too hard. With two arguments the problem gets a bit more challenging. With more than two arguments, testing every combination of appropriate values can be daunting.

Output arguments are harder to understand than input arguments. When we read a function, we are used to the idea of information going in to the function through arguments and out through the return value. We don’t usually expect information to be going out through the arguments. So output arguments often cause us to do a double-take.

##### Common Monadic Forms

There are two very common reasons to pass a single argument into a function. You may be asking a question about that argument, as in `boolean fileExists(“MyFile”)` . Or you may be operating on that argument, transforming it into something else and returning it. For example, `InputStream fileOpen(“MyFile”)` transforms a file name `String` into an `InputStream` return value. These two uses are what readers expect when they see a function. You should choose names that make the distinction clear, and always use the two forms in a consistent context.

##### Flag Arguments

Flag arguments are ugly. Passing a boolean into a function is a truly terrible practice. It immediately complicates the signature of the method, loudly proclaiming that this function does more than one thing. It does one thing if the flag is `true` and another if the flag is `false`!

##### Dyadic Functions

A function with two arguments is harder to understand than a monadic function. For example, `writeField(name)` is easier to understand than `writeField(output-Stream, name)`

There are times, of course, where two arguments are appropriate. For example,`Point p = new Point(0,0);` is perfectly reasonable. Cartesian points naturally take two arguments.

Even obvious dyadic functions like assertEquals(expected, actual) are problematic. How many times have you put the actual where the expected should be? The two arguments have no natural ordering. The expected, actual ordering is a convention that requires practice to learn.

Dyads aren’t evil, and you will certainly have to write them. However, you should be aware that they come at a cost and should take advantage of what mechanims may be available to you to convert them into monads. For example, you might make the writeField method a member of outputStream so that you can say outputStream. writeField(name) . Or you might make the outputStream a member variable of the current class so that you don’t have to pass it. Or you might extract a new class like FieldWriter that takes the outputStream in its constructor and has a write method.

##### Triads

Functions that take three arguments are significantly harder to understand than dyads. The issues of ordering, pausing, and ignoring are more than doubled. I suggest you think very carefully before creating a triad.

**[⬆ back to top](#table-of-contents)**

#### Argument Objects

**Bad:**
```java
Circle makeCircle(double x, double y, double radius);
```

**Good:**
```java
Circle makeCircle(Point center, double radius);
```

**[⬆ back to top](#table-of-contents)**

##### Verbs and Keywords
Choosing good names for a function can go a long way toward explaining the intent of the function and the order and intent of the arguments. In the case of a monad, the function and argument should form a very nice verb/noun pair. For example, `write(name)` is very evocative. Whatever this “name” thing is, it is being “written.” An even better name might be `writeField(name)` , which tells us that the "name" thing is a "field".

This last is an example of the keyword form of a function name. Using this form we encode the names of the arguments into the function name. For example, `assertEquals` might be better written as `assertExpectedEqualsActual(expected, actual)`. This strongly mitigates the problem of having to remember the ordering of the arguments.

**[⬆ back to top](#table-of-contents)**

### Output Arguments
In general output arguments should be avoided. If your function must change the state of something, have it change the state of its owning object.

**[⬆ back to top](#table-of-contents)**

### Command Query Separation
Functions should either do something or answer something, but not both. Either your function should change the state of an object, or it should return some information about that object. Doing both often leads to confusion.

**[⬆ back to top](#table-of-contents)**

### Prefer Exceptions to Returning Error Codes
Returning error codes from command functions is a subtle violation of command query separation.

**[⬆ back to top](#table-of-contents)**

### Don't Repeat Yourself
Duplication may be the root of all evil in software. Many principles and practices have been created for the purpose of controlling or eliminating it.

**[⬆ back to top](#table-of-contents)**

### Structured Programming
Some programmers follow Edsger Dijkstra’s rules of structured programming. Dijkstra said that every function, and every block within a function, should have one entry and one exit. Following these rules means that there should only be one return statement in a function, no `break` or `continue` statements in a loop, and never, ever, any `goto` statements.

While we are sympathetic to the goals and disciplines of structured programming, those rules serve little benefit when functions are very small. It is only in larger functions that such rules provide significant benefit.

So if you keep your functions small, then the occasional multiple `return` , `break` , or `continue` statement does no harm and can sometimes even be more expressive than the single-entry, single-exit rule. On the other hand, `goto` only makes sense in large functions, so it should be avoided

**[⬆ back to top](#table-of-contents)**

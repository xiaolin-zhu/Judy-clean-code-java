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

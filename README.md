# clean-code-java

## Table of Contents
  1. [Introduction](#introduction)
  2. [Variables](#variables)

## Introduction
Software engineering principles, from Robert C. Martin's book
[*Clean Code*](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882),
adapted for Java.

## **Variables**
### Use meaningful and pronounceable variable names

**Bad:**
```java
String yyyymmdstr = new SimpleDateFormat("YYYY/MM/DD").format(new Date());
```

**Good:**
```java
String currentDate = new SimpleDateFormat("YYYY/MM/DD").format(new Date());
```
**[⬆ back to top](#table-of-contents)**
# Singleton Lab

## Learning Goals

- Use the singleton pattern

## Introduction

We'll be creating a logging library. In our (simplified) case, logging requires
access to the console of the computer we're logging the output on.

## Instructions

We want our logger instance to be a singleton because we want to be able to
output the line numbers with each output statement and we want those line
numbers to be incremented across the entire system regardless of what class is
printing information out.

Hints:

- Call your class `Logger`.
- Everywhere you need access to the "logger", you will use the
  `Logger.getInstance()` method to get an instance of the Logger and then use
  whatever methods the logger provides to output statements to the console.
- Implement a `log()` method that takes a `String` parameter and output the line
  number before outputting the message passed in.

Your output from using your logger should look something like this:

```java
1::Sample output line 1
2::Second line of sample output
```

## Walkthrough

```java
public class Logger {
    private int currentLine = 0;
    private static Logger logger = null;

    private Logger() {
    }

    public static Logger getInstance() {
        if (logger == null) {
            logger = new Logger();
        }

        return logger;
    }

    public void log(String message) {
        currentLine++;
        System.out.println(currentLine + "::" + message);
    }
}
```

As we continue to build up code in this section on patterns, we will use the
`Logger` class we just created everywhere where we had previously used
`System.out.println()`.

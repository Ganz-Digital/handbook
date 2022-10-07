---
sidebar_label: Rules
---

# The Rules of Clear Code

## Introduction

Screen space is scarce.

This might sound strange because we all know that we can just scroll down to show more content. There is even something called infinite scroll. It works for social media companies because they don't need your attention span to be long.

It's another thing when we're coding or reading code, though. The goal there is to focus. In order to focus, there must be as little distraction as possible. Scrolling is a distraction, too.

We must make sure that every line in our code is justified. Every line must convey information.

Readers must be able to understand a piece of your code without having to scroll, without having to look up references, without having to check other files of the project. And without having a doubt about what the code does.

The following rules are supplemental to the usage of ESLint and Prettier.js.

## Naming

### Boolean variables must contain a modal verb.

By including a modal verb, readers can tell that the variable stores a boolean value without having to look at actual values or a type definition.

```jsx
// GOOD
const isActive = true;
const canChange = false;

// BAD
const active = true;
const changeable = false;
```

### Function names must include a verb and a noun.

A function always does something. You pass data to it, it transforms it and returns it. This is an action. The linguistic equivalent of an action is the verb. In Clear Code, function names always include a verb. Except for React components. They work better without a verb.

A function usually also does something with something. Thus, it needs a noun, too.

```jsx
// GOOD
function calculateOvertime() {
  // ...
}

// BAD
function overtime() {
  // ...
}

// BAD
function calculate() {
  // ...
}
```

:::info
This doesn't apply to React components. They can have names like `Home` and `EmployeeList`.
:::

### Function names must say what the function does.

A reader must be able to look at a function call and understand what it does without having to inspect the function itself.

Function names must therefore always state everything the function does – not more, not less.

```jsx
/**
 * GOOD: This function name describes everything that happens inside it.
 */
function createAndSendPushNotification() {
 // Create notification:
 ...
 // Send notification:
 ...
}

/**
 * BAD: This function not only creates a notification but also sends it.
 */
function createPush() {
  // Create notification:
 ...
 // Send notification:
 ...
}
```

### Variable names must describe what the variable contains.

As with function names, variable names must be accurate and convey meaning. They must be understandable without knowledge of any context.

Variable names don't include verbs.

```jsx
// GOOD: The name indicates that this is an array of IDs.
const employeeIDs = sessions.map((s) => s.employeeID);

// BAD: The name suggests that this is an array of employee objects.
const employees = sessions.map((s) => s.employeeID);
```

### No abbreviations.

You must not use abbreviations. Always write the whole word. Abbreviations increase the cognitive load for the reader and they are often ambiguous.

This counts everywhere apart from iterators.

```jsx
/**
 * GOOD
 * Readers who know how filter() works, understand that "s" is a session.
 */
sessions.filter((s) => s.employee === employeeID);

/**
 * BAD
 * To the writer, this might stand for "namespace".
 * For readers, "ns" is just two letters which mean more brain work.
 */
const ns = "common";
```

## Spacing

### No empty lines in functions.

Understanding code means creating a mental model of the code. It always starts with skimming through the code. The reader tries to get an overview of what's happening. In this process, it's very important to signal to the reader what belongs together.

In a function, everything should belong together. If it doesn't belong together, it should be split out into a separate function.

Of course there is a limit on how much splitting out into separate functions makes sense. Sometimes, you want to structure the contents of a function. You can do that: By adding a comment.

By adding a comment, you create a visual separation between some lines of code (which is what you want) _and_ explain why you think the separation is needed (which is what the reader wants).

```jsx
// GOOD
function calculateSalaryTotal() {
  const employeeSalaries = employees.map((e) => e.salary);
  const totalSalary = employeeSalaries.reduce((sum, salary) => (sum += salary));
  return totalSalary;
}

// GOOD (see rule "Comment the Why, not the What")
function calculateSalaryTotal() {
  const employeeSalaries = employees.map((e) => e.salary);
  // How much is the total salary?
  return employeeSalaries.reduce((sum, salary) => (sum += salary));
}

/**
 * BAD
 * When skimming through the code, the empty lines wrongly signals that a new function starts.
 */
function calculateSalaryTotal() {
  const salaries = employees.map((e) => e.salary);

  return salaries.reduce((sum, salary) => (sum += salary));
}
```

:::info
It's okay to have empty lines in React components.
:::

<!-- ## `function` vs `const`

Within a `function`, use `const` to define a function. Outside of a `function`, use `function`. -->

<!-- ## Use functional programming techniques.

Functional programming makes sure that the reader's eye does not have to jump up and down more than necessary. -->

## Commenting

### Comment the Why, not the What.

If functions and variables are named well, you make sure that someone who reads the code understands what it does.

What your code doesn't say, though, is _why_ it does what it does and _why_ it is written how it is written. This is what you have to explain in comments.

In comments, we give each other context. Decisions you have made while thinking deeply about to problem. Trade-offs you have made to get to a solution. Things like "This is just how it is".

:::tip
Write a comment for anything a reader can't find out by looking at the code but must know to understand the code.
:::

```jsx
/**
 * GOOD
 * This comment gives me context.
 */
function calculateSalaryTotal() {
  const employeeSalaries = employees.map((e) => e.salary); // This is the monthly salary in cents.
  const totalSalary = employeeSalaries.reduce((sum, salary) => (sum += salary));
  return totalSalary;
}

/**
 * BAD
 * These comments don't tell me anything that I
 * couldn't find out just from reading the code.
 */
function calculateSalaryTotal() {
  // Get salaries:
  const salaries = employees.map((e) => e.salary);
  // Calculate total:
  const totalSalary = salaries.reduce((sum, salary) => (sum += salary));
  return totalSalary;
}
```

## Export default functions directly.

## Define functions after calling them – if possible.

Humans read code from top to bottom. We structure our code to match this behaviour and make sure that we put the main concepts at the top and the details at the bottom.

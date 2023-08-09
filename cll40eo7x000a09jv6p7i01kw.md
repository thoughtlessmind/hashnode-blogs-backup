---
title: "Understanding  Function Overload in Typescript"
seoTitle: "What is function overload in typescript?"
seoDescription: "Function Overloads in Typescript allow to define multiple function signatures for the same function. Each signature specifies a particular set of parameters"
datePublished: Wed Aug 09 2023 17:33:44 GMT+0000 (Coordinated Universal Time)
cuid: cll40eo7x000a09jv6p7i01kw
slug: function-overload-in-typescript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691227799345/8a2ba547-9686-4817-8ad0-a28ec683cb87.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691602351304/b90a9185-61b0-46b2-bb86-6e3f5edff724.png
tags: javascript, typescript, functional-programming, frontend-development

---

### **What are Function Overloads?**

Function Overloads in Typescript allow us to define multiple function signatures for the same function. Each signature specifies a particular set of parameter types and the corresponding return type. This feature enables TypeScript to perform accurate type checking and inference, ensuring the function behaves correctly with different argument combinations.

*TLDR, Show me the code*: [TS Playground for example](https://www.typescriptlang.org/play?ssl=22&ssc=1&pln=12&pc=1#code/PTAEDEFcDsGMBcCWB7aoDOiDm0CG9IAnAU1ADNlDRcATGxaLUaSAWwCNjD1robQSBQtAZNczNp0IAoMjAQo0tGgApcALgkcuAGlDtNLbYQCUhyVwDc06SAjykqDNjxDSFKrFSx8xV6Ix4QlEeXD4BYiERRmpA4MZZB0VqOjVNdCDRPQM40TNcxmtbMCg4RzREVgAHABtiVj94fGT4AAt8UHa+Op52ZDbQH3RidESy5OU03gBPbM0w6fyF0ABvaVAIqNiAan1rAF8bOwB1RBqazaI0DPimRDJB1AA3LngAFWQAZUyYxB4gyDEMYKJxeaAvQjvZAAVRE8BUT1wNUB5mMejBEKh31umgBxHyN1ERTsAHczhdBFctFJQPdHuDXh9sQE-uQkcNgeV6ZiPrDEPDEcjiKipPkjFIinJxqDnoyYXCEUiUdTdI8eV8flgAPyaPrIOphEyrda0h4qLzq5mMI2U4SgQWAgB08A1txUJmsG1taAdxAONjBGW5r2INCtWAAakrSABeYOQ3kKgCMAAY9HiPcUNtmAHpagOoIMYkM0ABybCjQtAceLCfl-JUqczdmzoDzNmkQA)

### **How to Use Function Overloads**

We define multiple function signatures to use function overloads above the actual function implementation. Each signature is specific to a set of arguments and the expected return type. The function implementation follows these signatures and handles different cases accordingly.

```typescript
// Function signature for adding numbers and returning a number
function add(a: number, b: number): number;

// Function signature for concatenating strings and returning a string
function add(a: string, b: string): string;

// Function implementation that handles both cases
function add(a: any, b: any): any {
  return a + b;
}
```

Let's consider one more example.

```typescript
function convertToUnit(value: number, convertToString?: boolean) {
  if (convertToString) return value.toString();
  return value;
}
```

in this, `converToUnit` returns a union type of `string | number`, which loses the intellisense and other TS benefits. To overcome this, we can add the function signature for the functions based on `covertToString` parameter value.

```typescript
// Will return string if convertToString is true
function convertToUnit(value: number, convertToString: true): string;

// will return number if convertToString is false
function convertToUnit(value: number): number;

function convertToUnit(value: number, covertToString?: boolean) {
  if (covertToString) return value.toString();
  return value;
}
```

the `convertedStringValue` would have all the intellisense for strings and `convertedNumValue` would have all the intellisense for numbers.

[TS Playground](https://www.typescriptlang.org/play?#code/PTAEDEFcDsGMBcCWB7aoDOiDm0CG9IAnAU1ADNlDRcATGxaLUaSAWwCNjD1robQSBQtAZNczNp0IAoMjAQo0tGgApcALgkcuAGlDtNLbYQCUhyVwDc06SAjykqDNjxDSFKrFSx8xV6Ix4QlEeXD4BYiERRmpA4MZZB0VqOjVNdCDRPQM40TNcxmtbMCg4RzREVgAHABtiVj94fGT4AAt8UHa+Op52ZDbQH3RidESy5OU03gBPbM0w6fyF0ABvaVAIqNiAan1rAF8bOwB1RBqazaI0DPimRDJB1AA3LngAFWQAZUyYxB4gyDEMYKJxeaAvQjvZAAVRE8BUT1wNUB5mMejBEKh31umgBxHyN1ERTsAHczhdBFctFJQPdHuDXh9sQE-uQkcNgeV6ZiPrDEPDEcjiKipPkjFIinJxqDnoyYXCEUiUdTdI8eV8flgAPyaPrIOphEyrda0h4qLzq5mMI2U4SgQWAgB08A1txUJmsG1taAdxAONjBGW5r2INCtWAAakrSABeYOQ3kKgCMAAY9HiPcUNtmAHpagOoIMYkM0ABybCjQtAceLCfl-JUqczdmzoDzNmkQA)
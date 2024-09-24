2024/09/20 02:41
Status: #idea
Tags: [[Typescript Fundamentals]]

## TypeScript Type Operators and Modifiers

TypeScript provides several operators and modifiers to create more complex and flexible types. Here are some of the most commonly used ones:

### 1. Optional Properties (?)

The question mark (?) makes a property optional:

```typescript
interface User {
  name: string;
  age?: number;  // age is optional
}

const user: User = { name: "Alice" };  // Valid, age is not required
```

### 2. Union Types (|)

The pipe symbol (|) allows a value to be one of several types:

```typescript
type StringOrNumber = string | number;

function printId(id: StringOrNumber) {
  console.log(`ID is: ${id}`);
}

printId(101);  // Valid
printId("202");  // Also valid
```

### 3. Intersection Types (&)

The ampersand (&) combines multiple types into one:

```typescript
interface Colorful {
  color: string;
}

interface Circle {
  radius: number;
}

type ColorfulCircle = Colorful & Circle;

const cc: ColorfulCircle = {
  color: "red",
  radius: 42
};
```

### 4. Type Assertions (as)

Type assertions tell TypeScript to treat a value as a specific type:

```typescript
let someValue: unknown = "this is a string";
let strLength: number = (someValue as string).length;
```

### 5. Non-null Assertion Operator (!)

The exclamation mark (!) removes null and undefined from a type:

```typescript
function getValue(): string | null {
  return "hello";
}

const str: string = getValue()!;  // Asserts that getValue() will not return null
```

### 6. Keyof Operator

`keyof` creates a union type of all the keys in an object type:

```typescript
interface Person {
  name: string;
  age: number;
}

type PersonKeys = keyof Person;  // "name" | "age"

function getProperty(obj: Person, key: PersonKeys) {
  return obj[key];
}
```

### 7. Typeof Operator

`typeof` can be used in type contexts to refer to the type of a variable:

```typescript
const myObj = { foo: "bar", baz: 42 };
type MyObjType = typeof myObj;  // { foo: string, baz: number }
```

### 8. Indexed Access Types

You can use indexing to access a specific property's type:

```typescript
type Person = { age: number; name: string; alive: boolean };
type Age = Person["age"];  // number
```

### 9. Conditional Types

Conditional types select one of two possible types based on a condition:

```typescript
type IsString<T> = T extends string ? true : false;

type A = IsString<string>;  // true
type B = IsString<number>;  // false
```

### 10. Mapped Types

Mapped types allow you to create new types based on old ones:

```typescript
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};

interface Writeable {
  name: string;
  age: number;
}

type ReadonlyPerson = Readonly<Writeable>;
// { readonly name: string; readonly age: number; }
```

These type operators and modifiers allow you to create more expressive and precise types in TypeScript, leading to safer and more self-documenting code. They're particularly useful in complex scenarios like working with APIs, creating reusable utility types, or modeling intricate domain logic.




---
# References

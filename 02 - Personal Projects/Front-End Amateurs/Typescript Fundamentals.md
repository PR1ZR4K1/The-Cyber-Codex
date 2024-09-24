2024/09/20 02:35
Status: #idea
Tags:

# TypeScript in Web Development: Key Concepts

## 1. Basic Types

TypeScript provides several basic types for use in your code:

- `boolean`: true or false values
- `number`: numeric values
- `string`: text values
- `array`: collections of values, can be typed as `Type[]` or `Array<Type>`
- `tuple`: fixed-length arrays with specified types for each index
- `enum`: a set of named constants
- `any`: a type that can be anything
- `void`: typically used as the return type of functions that do not return a value
- `null` and `undefined`: subtypes of all other types

Example:

```typescript
let isDone: boolean = false;
let decimal: number = 6;
let color: string = "blue";
let list: number[] = [1, 2, 3];
let x: [string, number] = ["hello", 10];
enum Color {Red, Green, Blue}
let notSure: any = 4;
function warnUser(): void {
    console.log("This is a warning message");
}
```

## 2. Interfaces vs Types

### Interfaces

Interfaces are used to define the structure of objects:

```typescript
interface User {
  name: string;
  age: number;
}
```

### Types

Types can define object structures and more complex types:

```typescript
type User = {
  name: string;
  age: number;
};

type Status = "pending" | "approved" | "rejected";
```

### Key Differences

1. Interfaces can be extended, types can use intersections
2. Interfaces support declaration merging, types do not
3. Types can create more complex structures like unions

## 3. Functions

TypeScript allows for typing function parameters and return values:

```typescript
function add(x: number, y: number): number {
    return x + y;
}

// Arrow function
const multiply = (x: number, y: number): number => x * y;

// Optional and default parameters
function buildName(firstName: string, lastName?: string): string {
    return lastName ? `${firstName} ${lastName}` : firstName;
}

// Rest parameters
function sum(...numbers: number[]): number {
    return numbers.reduce((total, n) => total + n, 0);
}
```

## 4. React Components in TypeScript

### Functional Components

There are multiple ways to type React functional components:

```typescript
// Using React.FC (Function Component)
const Greeting: React.FC<{ name: string }> = ({ name }) => <h1>Hello, {name}!</h1>;

// Using a separate interface
interface GreetingProps {
  name: string;
}

const Greeting = ({ name }: GreetingProps) => <h1>Hello, {name}!</h1>;

// Inline prop typing
const Greeting = ({ name }: { name: string }) => <h1>Hello, {name}!</h1>;
```

### Class Components

For class components, you can use interfaces to define props and state:

```typescript
interface Props {
  name: string;
}

interface State {
  count: number;
}

class Counter extends React.Component<Props, State> {
  state: State = {
    count: 0
  };

  render() {
    return <div>Count: {this.state.count}</div>;
  }
}
```

## 5. Generics

Generics allow you to create reusable components:

```typescript
function identity<T>(arg: T): T {
    return arg;
}

// Usage
let output = identity<string>("myString");
```

In React:

```typescript
interface Props<T> {
  items: T[];
  renderItem: (item: T) => React.ReactNode;
}

function List<T>({ items, renderItem }: Props<T>) {
  return (
    <ul>
      {items.map((item, index) => (
        <li key={index}>{renderItem(item)}</li>
      ))}
    </ul>
  );
}
```

## 6. Spread Operator

The spread operator (`...`) is useful in many scenarios:

1. Arrays:
```ts
const fruits = ['apple', 'banana'];
const moreFruits = ['orange', ...fruits, 'grape'];

console.log(moreFruits);
```

Output:
```ts
['orange', 'apple', 'banana', 'grape']
```
Explanation: The spread operator `...fruits` unpacks the elements of the `fruits` array into the `moreFruits` array. The resulting array contains 'orange' at the beginning, followed by all elements from `fruits`, and 'grape' at the end.

2. Objects:
```ts
const person = { name: 'Alice', age: 30 };
const employee = { ...person, job: 'Developer' };

console.log(employee);
```

Output:
```ts
{ name: 'Alice', age: 30, job: 'Developer' }
```
Explanation: The spread operator `...person` copies all properties from the `person` object into the `employee` object. Then, the `job` property is added. If there were any conflicts (i.e., if `person` already had a `job` property), the new value would overwrite the spread value.

3. Function arguments:
```typescript
function sum(...numbers: number[]): number {
  return numbers.reduce((total, n) => total + n, 0);
}

console.log(sum(1, 2, 3, 4, 5));
```

Output:
```
15
```
Explanation: The spread operator in the function parameter `...numbers` allows the function to accept any number of arguments. All arguments passed to the function are collected into an array named `numbers`. The function then uses the `reduce` method to sum up all the numbers in this array.

You could also call this function with an existing array using the spread operator:

```typescript
const nums = [1, 2, 3, 4, 5];
console.log(sum(...nums));
```

Output:
```
15
```
In this case, the spread operator is used when calling the function, spreading the elements of the `nums` array as individual arguments to the `sum` function.

In React:

```typescript
const Button = ({ text, onClick, ...restProps }: ButtonProps) => (
  <button onClick={onClick} {...restProps}>{text}</button>
);
```

## 7. TypeScript in Next.js

Next.js has built-in TypeScript support. Some Next.js-specific types include:

```typescript
import { GetServerSideProps, GetStaticProps, NextPage } from 'next';

// For server-side rendering
export const getServerSideProps: GetServerSideProps = async (context) => {
  // ...
}

// For static site generation
export const getStaticProps: GetStaticProps = async (context) => {
  // ...
}

// Typing a page component
const Home: NextPage = () => {
  // ...
}
```

Remember to use `.tsx` extension for files containing JSX.





---
# References

- [[Typescript Operators]]
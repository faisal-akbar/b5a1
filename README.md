### What is the use of the keyof keyword in TypeScript? Provide an example.
The `keyof` in TypeScript is used to create a union type of the keys of an object type. It helps to create union type dynamically based on the keys of an object. This is particularly useful when we want to create functions with generic.

For example, consider the following code:

```typescript
type Person = {
  name: string;
  age: number;
  email: string;
};

type PersonKeys = keyof Person; // "name" | "age" | "email"

const person: Person = {
  name: "Anders Hejlsberg",
  age: 64,
  email: "anders@example.com",
};

// Function to get value by key
function getValueByKey<T>(obj: T, key: keyof T): T[keyof T] {
  return obj[key];
}

const name = getValueByKey(person, "name"); 
const age = getValueByKey(person, "age"); 
const email = getValueByKey(person, "email"); 
console.log(name); // Output: Anders Hejlsberg
console.log(age); // Output: 64
console.log(email); // Output: anders@example.com
```

In this above example, we define a `Person` type with three properties: `name`, `age`, and `email`. We then use the `keyof` to create a new type `PersonKeys`, which provide union of the keys of the `Person` type. The `getValueByKey` function takes an object of type `T` and a key of type `keyof T`, and returns the value for that key.


### Provide an example of using union and intersection types in TypeScript.
Union and intersection types in TypeScript are used to combine multiple types into one.
Union Types- union types help to define new types that can have multiple types. We use the `|` operator to create a union type. Union types are or either, meaning that a variable can be of one type or another.
Intersection Types- Intersection types help to define new types that combine multiple types. We use the `&` operator to create an intersection type. Intersection types are and, meaning that a variable must satisfy all the types in the intersection.

Example of Union Types:
```typescript
type Person = {
  name: string;
  age: number;
};
type Employee = {
  employeeId: number;
  department: string;
};
type PersonOrEmployee = Person | Employee;
const person: Person = {
  name: "Anders Hejlsberg",
  age: 64,
};
const employee: Employee = {
  employeeId: 12345,
  department: "Engineering",
};
```

Example of Intersection Types:
```typescript
type Person = {
  name: string;
  age: number;
};
type Employee = {
  employeeId: number;
  department: string;
};
type EmployeeDetails = Person & Employee;
const employee: EmployeeDetails = {
  name: "Anders Hejlsberg",
  age: 64,
  employeeId: 12345,
  department: "Engineering",
};
```

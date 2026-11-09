# type vs interface

mainly both `type` and `interface` can be used to define the structure of data, like which properties they can have and what data type they can hold, like string, number, or boolean. but there is a difference also between them. both can define object structure, but `type` aliases can also be used with union types, primitive types, and tuples.

for simple object shapes, both work fine. i can use either one, but i try to stay consistent.

examples:

```ts
// using interface
interface User {
  name: string;
  age: number;
}

// using type
type Account = {
  name: string;
  age: number;
};
```

```ts
// type aliases with union
type Status = 'success' | 'error' | 'loading';

// tuple types
type UserInfo = [string, number, boolean];

// primitive
type UserId = number;
```

another difference is `interface` supports declaration merging. if we declare the same interface twice, TypeScript merges the properties. but if we declare the same `type` twice, it gives an error.

```ts
interface Profile {
  name: string;
}

interface Profile {
  age: number;
}

// Profile now has both name and age
```

`interface` is also better when other code may add more properties to the same type later. `type` is useful when a value can be one of a few fixed options, like a status.

so i use `interface` for object structure and `type` for union, tuple, primitive.

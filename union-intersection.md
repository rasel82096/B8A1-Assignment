# Union (`|`) and Intersection (`&`) Types

Here ,union (`|`) and intersection (`&`) types are used to combine types in TypeScript, but they work differently.

`union (|)` means a value can be one of multiple types, while `intersection (&)` means a value must satisfy all the combined types.

for example, suppose we have two types, `User` and `Admin`. we can use intersection to combine their properties and union to allow a value to be either a `User` object or an `Admin` object.

examples:

```ts
type User = {
  name: string;
  email: string;
};

type Admin = {
  permissions: string[];
};

// intersection: must have all properties
type AdminUser = User & Admin;

// union: can be either User or Admin
type Account = User | Admin;

const admin: AdminUser = {
  name: "Rasel",
  email: "rasel@example.com",
  permissions: ["read", "write"]
};

const account: Account = {
  name: "Rasel",
  email: "rasel@example.com"
};

const adminAccount: Account = {
  permissions: ["read"]
};
```

here, `AdminUser` must have all properties from both `User` and `Admin`. but `Account` can be either a `User` or an `Admin`.

also, `User | Admin` doesn't mean the object needs all properties. it just needs to match at least one type. if we want all properties, we use `&`. for example, an admin account can be just `{ permissions: ["read"] }`.

so basically, we use `union (|)` when a value can have different possible types, and `intersection (&)` when i want to combine multiple types into one.

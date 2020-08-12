# Optional Function Parameters

## The Problem

```js
doSomething((unused1, unused2, somethingUseful) => {
  doSomethingWith(somethingUseful);
});

doSomething((_, __, somethingUseful) => {
  doSomethingWith(somethingUseful);
});
```

## Solutions

### Elisions

```js
doSomething(( , , somethingUseful) => {
  doSomethingWith(somethingUseful);
});
```

- Matches with existing destructuring
  - `([, c])` is already valid
- Some might say it looks weird

### Placeholder Syntax

```js
doSomething((?, ?, somethingUseful) => {
  doSomethingWith(somethingUseful);
});

doSomething((*, *, somethingUseful) => {
  doSomethingWith(somethingUseful);
});

// etc.
```

- Requires more syntax

### Placeholder Identifier

```js
doSomething((_, _, somethingUseful) => {
  doSomethingWith(somethingUseful);
});

doSomething((_, _, somethingUseful) => {
  print(_); // IdentifierReference : `_` early error?
  doSomethingWith(somethingUseful);
});
```

- Any valid identifiers are already valid identifiers, could conflict with existing code

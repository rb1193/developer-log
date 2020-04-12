# Javascript Language

When assigning an object property to another variable in Javascript, the reference is maintained by default. You need to copy the variable somehow to break the reference

Using an async function with an await call as an `Array.prototype.forEach()` callback doesn’t really work, as the callback itself is not awaited by the underlying forEach code. To get around this, you can use `Promise.all(array.map(asyncCallback))`

Nested promises (i.e. then functions inside then or catch clauses) are an anti-pattern. End the chain by setting a variable outside the scope of the promise chain and then using that value synchronously

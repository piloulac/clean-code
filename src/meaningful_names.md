## Meaningful Names
> "Names are everywhere in software"

> "You will use them every time, so take the time to choose them. Code is not only for compilers."

### Intention-revealing names
```ts
// TS
const d: number; // time elapsed
```
Should be:
```ts
// TS
const timeElapsedSinceCreation: number;
```
### Avoid desinsformation
Programmers must avoid leaving false clues that obscure the meaning of code. We should avoid words whose entrenched meanings vary from our intended meaning. Avoid using:
```ts
// TS
const accountsList: Set<Account>; 
```
Should only be named so if it is a actually a list data structure that’s used to store the accounts. Not an array or set.
### Pronounceable names
When you will be discussing the variable you will hate to talk about
```ts
// TS
const genydhms: number;
```
but 
```ts
// TS
const generationTimestamp: number;
```
### Searchable name
Avoid single letter variables and constants as they are difficult to search.

### Pick one work per concept
Pick one word for one abstract concept and stick with it: `fetch`, `retrieve` or `get`? Make your choice.

It’s confusing to have a controller and a manager and a driver in the same
code base. What is the essential difference between a `DeviceManager` and a `ProtocolController`?

### Names
1. Class name should be **noun** (or noun phrases)
1. Function name should be **verb** (or verb phrases)


> "If at any moment you find a name that better represents your object. **Changes it**."
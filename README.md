# JS proposal - object equality
JS proposal for TC39

## Proposer
Marina Timofeeva, WG-Forge JS junior developer :)

## Status
This proposal is a stage: -1 proposal and waiting for feedback.

## Motivation
Today we don't have straightforward way to check if two objects are equal, it get more messier to check when objects has deeply nested objects.

## Short description
Now there is the most simple and fast way to compare 2 objects:
JSON.stringify(obj1) === JSON.stringify(obj2) //true
But it has one big drawback: if we swap the keys in the objects, it won't work and we get false.
 x = {a: 1, b: 2};
 y = {b: 2, a: 1};
JSON.stringify(x) === JSON.stringify(y) //false

The most generic way is to write own method, that compares properties' projections recursively, and also compares constructors. But it's not easy to do.
This problem is covered well by libraries like Lodash, Underscore. But it's not always convenient to use libraries.

So It would be nice to have native js method to compare objects, using existing syntax with "===" that will give the resalt of deep equality.

## Example

 x = {a: 1, b: 2};
 y = {b: 2, a: 1};
 
 x === y // true
 
 x = {a: 1, b: 2};
 y = {a: 1, b: 2};
 
 x === y // true
 
 x = {a: 1, b: 2};
 y = {a: 5, b: 2};
 
 x === y // false
 
 x = 
 {a: 1,
  b: {
    c: 5
  }
 };
 x = 
 {a: 1,
  b: {
    c: 5
  }
 };
 
 x === y // true

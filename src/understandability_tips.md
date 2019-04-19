## Understandability tips
> IN PROGRESS
1. Be consistent. If you do something a certain way, do all similar things in the same way.
1. Use explanatory variables.
1. Encapsulate boundary conditions. Boundary conditions are hard to keep track of. Put the processing for them in one place.
1. Prefer dedicated value objects to primitive type.
1. Avoid logical dependency. Don't write methods which works correctly depending on something else in the same class.
1. Avoid negative conditionals.
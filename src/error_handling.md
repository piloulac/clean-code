##  Error Handling
### Use exception rather than return codes.
Using errors
```java
// JAVA
if(doSomething()){
    if(doSomethingElse()){
        if(doSomethingElseAgain()){
            // fool
        } else {
            // react to failure of doSomethingElseAgain
        }
    } else {
        // react to failure of doSomethingElse
    }
} else {
    // doSomething
}
```
To make things right, write your try-catch-finally first and use exceptions.
```java
// JAVA
try {
    doSomething();
    doSomethingElse();
    doSomethingElseAgain();
} catch(const SomethingException &e){

} catch(const SomethingElseException &e){
    
} catch(const SomethingElseAgainException &e){
```

### Don't pass null
Do not return or pass `null`. You should better use an empty version of the type that is being expected.

```java
// JAVA
public static Collection restoreCollection (String stringRepresentation) {
    ...
    if(stringRepresentation != null){
        ...
    } else {
        return null;
    }
}
```
You have to check for `null` and you'll get errors because of it.
```java
// JAVA
public static Collection restoreCollection (String stringRepresentation) {
    ...
    if(stringRepresentation.isEmpty()){
        ...
    } else {
        return new Emptycollection();
    }
}
```
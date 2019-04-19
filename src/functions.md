## Function
> "Functions should do one thing. They should do it well. They should do it only."

Functions are the first line of organisation in any program. They should follow the basic rules

1. One level of abstraction per function
1. Do one thing only (error handling is one thing). If a function has try keyword then it should be the very first keyword and there should be nothing after the catch/finally blocks.
1. Read code from top to bottom (like book)
1. Use descriptive names

Move from
```java
// JAVA
public void delete(String path) { 
  Page page = getPage(path);
  try {
    deletePage(page);
    registry.deleteReference(page.name); 
    configKeys.deleteKey(page.name.makeKey());
  }
  catch (Exception e) { 
    logger.log(e.getMessage());
  } 
  notifyPageDelete();
  reload();
}
```
To 
```java
// JAVA
// remove getPage, notifyPageDelete and reload from the delete method
public void delete(Page page) { 
  try {
     deletePageAndAllReferences(page);
  }
  catch (Exception e) { 
    logError(e);
  } 
}

private void deletePageAndAllReferences(Page page) throws Exception { 
    deletePage(page);
    registry.deleteReference(page.name); 
    configKeys.deleteKey(page.name.makeKey());
}

private void logError(Exception e) { 
    logger.log(e.getMessage());
}
```

### Function argument
Try to minimise as mush as possible the number of arguments! More than 2 arguments means that you should refactor something.
```ts
// TS
const createSpecialOffer = (
    mytype: string;
    maxRenewals: number;
    couponDuration?: string;
    duration: Duration;
    redeemType: string;
    newUserOnly: boolean;
    newUserMaxAge?: number;
    isPremiumPlus: boolean;
    callback: Callback<SpecialOffer>
) => {
    // do things
}
```
Is complicated to use and read from. Try to extract argument or use object params.
```ts
// TS
const createSpecialOffer = ( 
    params: {
        mytype: string;
        maxRenewals: number;
        couponDuration?: string;
        duration: Duration;
        redeemType: string;
        newUserOnly: boolean;
        newUserMaxAge?: number;
        isPremiumPlus: boolean;
    },
    callback: Callback<SpecialOffer>
) => {
    // do things
}
```

### Verb and keyword
Functions’ verb and arguments must mean something. Argument must be keywords of the verb! Avoid a,b,c,etc…(except for iterator) 

### Have no side effect
A function do only one thing! It must not do something else! Side effects are hidden errors. Having `getPage` which actually `INSERT INTO` something.

### Prefere exception to returning error
Functions do something or answer something, not both. Returning error is a subtle violation of command query.

> "Master programmers think of systems as stories to be told rather than programs to be written."

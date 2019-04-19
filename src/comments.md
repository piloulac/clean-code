## Comments
>  “Comments Do not Make Up for Bad Code”

### Explain yourself in code
If you need a comment it means that your code is not clear enough.

```java
// JAVA
try {
    int response_code = conn.getResponseCode();
    // Check if successful connection made
    if(response_code == 200) {
        // Read data sent from server
        InputStream input = conn.getInputStream();
        BufferedReader reader = new BufferedReader(new InputStreamReader(input));
        StringBuilder result = new StringBuilder();
        String line;
        while ((line = reader.readLine()) != null){
            resul.append(line);
        }
        // Pass data to onPostExecute method
        return (result.toString());
    } else {
        return 'unsuccessful';
    }
} catch(IOException e){}
```

Shows 3 useless comments

```java
// JAVA
try {
    int response_code = conn.getResponseCode();
    if(connectionIsSuccessful(response_code)) {
        return readDataSentFromServer(conn.getInputStream());
    } else {
        return 'unsuccessful';
    }
} catch(IOException e){}


Boolean connectionIsSuccessful (int response_code) {
    return response_code == 200;
}

String readDataSentFromServer(InputStream input) {
    InputStream input = conn.getInputStream();
    BufferedReader reader = new BufferedReader(new InputStreamReader(input));
    StringBuilder result = new StringBuilder();
    String line;
    while ((line = reader.readLine()) != null){
        resul.append(line);
    }
    return line;
}
```

### Avoid redondant and noise comments
Really avoid those kind of comments...
```java
// JAVA
// create cart entity
Cart cart = new Cart();
```

```java
// JAVA
@Override
public void onClick(View view, int position) {
    // The onClick implementation of the RecyclerView item click
    final Game game = mGames.get(position);
    ....
}
```

### Don't believe that you're writing a public API (except if it's the case)
Should only as specific if it is exposed.
```ts
// TS
export interface Output {
    /**
     * List of api keys
     */
    apiKeys: {
        /**
         * The id of the api key
         */
        id: number;
        /**
         * The creation date
         */
        creationDateUnix: number;
        /**
         * The last modification date
         */
        updateDateUnix: number;
        /**
         * The last invalidation date
         */
        invalidationDateUnix: null | number;
        /**
         * The name of the partner
         */
        partnerName: string;
        /**
         * The access key
         */
        accessKey: string;
        /**
         * Is the API key activated or not
         */
        valid: boolean;
    }[];
}
```

### Comments should not reflect your laziness
Avoid commented-out code: what does it reflect? is it important? Do we need to let it?
```java
// JAVA
@Override
public void onClick(View view, int position) {
    // The onClick implementation of the RecyclerView item click
    final Game game = mGames.get(position);
    ....
    startActivityForResult(i, REQUEST_CODE_CART_UPDATE);
    // startActivity(i);
}
```

Todo: you will forget it! Do it right now or at least use a TODO marker/
```java
// JAVA
if(resultCode == Activity.RESULT_CANCELTED){
    // write your code if there's no result
}
```

### There are good comments. 
Of course, there are good comments

1. legal comments
1. **informative & explanation of intent**: Should always contain a word like: *because, thanks, to, as, etc...*
1. public API
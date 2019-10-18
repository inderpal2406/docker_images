## Lab 14
This is to demonstrate use of `ENV` instruction.

* The `ENV` instruction in Dockerfile sets the environment variable for our container when we start.
* The default value can be overridden by passing --env <key>=<value> when we start the container.

## Commands
```
 docker build -t inderpal2406/alpine-env:v0.0.1 .
 docker run inderpal2406/alpine-env:v0.0.1
 ```

 ## Output of container
 ```
 This is display message.
 ```

 ## Overriding ENV variable
 ```
 docker run --env MESSAGE="This is new display message." inderpal2406/alpine-env:v0.0.1
 ```

 ## Output of Overriding
 ```
 This is new display message.
 ```

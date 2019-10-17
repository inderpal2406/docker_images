## Lab 9
To demonstrate use of `WORKDIR` instruction with relative path.

* The `WORKDIR` directive in Dockerfile defines the working directory for the rest of the instructions in the Dockerfile.
* We can have multiple `WORKDIR` in same Dockerfile.
* If a relative path is provided, it will be relative to the previous `WORKDIR` instruction.
* If no `WORKDIR` is specified in the Dockerfile then the default path is `/`.
* The `WORKDIR` instruction can resolve environment variables previously set in Dockerfile using `ENV`.

## Commands
```
docker build -t inderpal2406/alpine-workdir:v0.0.2 .
docker run inderpal2406/alpine-workdir:v0.0.2
```

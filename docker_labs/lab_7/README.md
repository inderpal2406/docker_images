## Lab 7
This is to demonstrate use of `ENTRYPOINT` instruction in shell form.

## Commands
```
docker build -t inderpal2406/alpine-entrypoint:v0.0.2 .
docker run inderpal2406/alpine-entrypoint:v0.0.2 .
```

## Override an existing ENTRYPOINT
`docker run --entrypoint "/bin/echo" inderpal2406/alpine-entrypoint:v0.0.2 "Hello World!"`

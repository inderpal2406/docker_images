# Lab 12
To demonstrate usr of `ARG` instruction.

## Commands
```
docker build -t inderpal2406/alpine-arg:v0.0.1 .
docker run inderpal2406/alpine-arg:v0.0.1
```

We get the below output:
```
/home/inder
Hello Inderpal Singh
```

* So, we can specify multiple commands separated by `;` in `CMD` section to execute multiple commands when container starts.
* Also, vaues of `ARG` variables can be defined in double quotes.

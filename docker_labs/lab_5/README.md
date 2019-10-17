## Lab 5
This is to demonstrate use of `CMD` instruction.

## Commands
```
docker build -t inderpal2406/alpine-cmd:v0.0.1 . -f Dockerfile_cmd
docker run inderpal2406/alpine-cmd:v0.0.1
```
This'll display top command output from within the container. When we press CTRL+C to come out of `top` command, the container exits.

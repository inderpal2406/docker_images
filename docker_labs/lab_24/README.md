## Lab 24
To construct a Docker image similar to hello-world, which will greet user when container is spinned from it.

We'll be using python for this.

## Dockerfile
```
FROM alpine:latest
LABEL NAME="python-hello-app"
ARG DIR="/mydir"
RUN \
  apk update && \
  apk add python && \
  mkdir $DIR
WORKDIR $DIR
COPY hello.py .
CMD [ "/mydir/hello.py"]
ENTRYPOINT [ "python" ]
```

## Commands
```
docker build -t inderpal2406/python-hello-app:v0.0.1 .
docker run inderpal2406/python-hello-app:v0.0.1
```

* Container ran successfuy and executed the `hello.py` script which displayed the message in the script.
* We can override `hello.py` script with command line argument.
* The `hello.py` script is specified in `CMD` instruction.
* To override it with another script, we can execute below command, <br>
`docker run inderpal2406/python-hello-app:v0.0.1 add.py` <br>
* Above overriding will work only if `add.py` is copied to the `WORKDIR` while copying `hello.py` while building the image.
* Likewise to override with any other python script, we need to have that script baked inside the image.
* Or we can override with python commands, <br>
```
docker run inderpal2406/python-hello-app:v0.0.1 --version
OUTPUT: Python 2.7.16
```
* However, supplying `docker run inderpal2406/python-hello-app:v0.0.1 print ("Hello")`, didn't work. But simply executing `python print ("Hello")` also doesn't work. So, we will stick to basic commands ike `--version` for now as overriding option apart from baked in scripts.

## Lab 2
In this lab, we'll learn using `ADD` instruction in Dockerfile.

## Commands
```
echo "This is to demonstrate ADD instruction." > message.txt
tar -cvf message.tar message.txt
docker build -t inderpal2406/alpine-add:v0.0.1 .
docker run --name alpine-add -dit inderpal2406/alpine-add:v0.0.1
docker ps
docker attach xxxx
pwd
ls -l
cat message.txt
```
We could see our `message.txt` file. We should note that it was already extracted by ADD command and added as a text file inside the container.

However, when I updated ADD instruction in Dockerfile with `ADD http://www.vlsitechnology.org/pharosc_8.4.tar.gz .`, the gzip file was downloaded and added to the container image. When I ran a container, I could see the pharosc_8.4.tar.gz file. It was not in extracted form.

To test further, I added a message.tar in local host. Further gzipped it to message.tar.gz. Add gzip file to image. Ran a container from image. Listed files in container and saw the message.tar file. So, it was extracted.

So,
* Docker may not extract remotely downloaded files.
* The default working directory of docker is `/`

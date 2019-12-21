## Jenkins Slave

- This [Dockerfile](Dockerfile) is used to build an image based on centOS with ssh installed in it.
- We can generate ssh keys, copy public key to this image (as specified in Dockerfile).
- Later private key can be used to ssh to docker container.
- This was used to enable `jenkins` user from jenkins container to ssh to an additional host using a private key (and not password) for remote execution of jenkins job.

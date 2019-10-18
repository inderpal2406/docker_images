## Lab 22
`USER` instruction

* The `USER` directive is similar to `WORKDIR`, which changes the state of the environment and affects future layers.
* `WORKDIR` is to change the working directory, and `USER` is the identity of the commands such as `RUN`, `CMD` and `ENTRYPOINT`.
* By default working directory is `/` and user is `root` unless specified otherwise.
* Like `WORKDIR`, `USER` just helps us to switch to the specified user. This user must be pre-established, otherwise it cannot be switched.

Example, <br>
```
FROM redis:latest
RUN \
  groupadd -r redis && \
  useradd -r -g redis redis
USER redis
CMD [ "redis-server" ]
```

If the script executed with root wants to change the identity during execution, such as wanting to run a service process with an already established user, don’t use su or sudo, which requires a more cumbersome configuration. And often in the absence of TTY environment. It is recommended to use [gosu] (https://github.com/tianon/gosu).

```
# Create a redis user and use gosu to change another user to execute the command
RUN groupadd -r redis && useradd -r -g redis redis
# download gosu
RUN wget -O /usr/local/bin/gosu "https://github.com/tianon/gosu/releases/download/1.7/gosu-amd64" \
    && chmod +x /usr/local/bin/gosu \
    && gosu nobody true
# Set CMD and execute it as another user
CMD [ "exec", "gosu", "redis", "redis-server" ]
```

Only this much was provided on website, need to try and understand more on our own.

## Lab 19
`HEALTHCHECK` instruction.

* The `HEALTHCHECK` directive tells Docker how to determine if the state of the container is normal.
* Before the `HEALTHCHECK` directive, the Docker engine can only determine if the container is in a state of abnormality by whether the main process in the container exits.
* In many cases, this is fine, but if the program enters a deadlock state, or an infinite loop state, the application process does not exit, but the container is no longer able to provide services.
* Prior to 1.12, Docker did not detect this state of the container and would not reschedule it, causing some containers to be unable to serve, but still accepting user requests.

## Syntax

`HEALTHCHECK [options] CMD <command>:`

The above syntax set the command to check the health of the container.

## How does it work?
When a `HEALTHCHECK` instruction is specified in an image, the container is started with it, the initial state will be starting, and will become healthy after the `HEALTHCHECK` instruction is checked successfully. If it fails for a certain number of times, it will become unhealthy.

## What options does HEALTHCHECK support?
* `--interval=<interval>`: interval between two health checks, the default is 30 seconds.
* `--timeout=<time length>`: The health check command runs the timeout period. If this time is exceeded, the health check is regarded as a failure. The default is 30 seconds.
* `--retries=<number>`: When the specified number of consecutive failures, the container status is treated as unhealthy, the default is 3 times.

**Like `CMD`, `ENTRYPOINT`, `HEALTHCHECK` can only appear once. If more than one is written, only the last one will take effect.**

Pending to be understood: https://dockerlabs.collabnix.com/beginners/dockerfile/healthcheck.html

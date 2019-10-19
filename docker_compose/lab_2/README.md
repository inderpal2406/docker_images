## Lab 2

## `help` command
The `docker-compose help` list out all the subcommands that can be used with docker-compose. We can even try `--help` or `-h` options.

```
$ docker-compose help
Define and run multi-container applications with Docker.

Usage:
  docker-compose [-f <arg>...] [options] [COMMAND] [ARGS...]
  docker-compose -h|--help

Options:
  -f, --file FILE             Specify an alternate compose file
                              (default: docker-compose.yml)
  -p, --project-name NAME     Specify an alternate project name
                              (default: directory name)
  --verbose                   Show more output
  --log-level LEVEL           Set log level (DEBUG, INFO, WARNING, ERROR, CRITICAL)
  --no-ansi                   Do not print ANSI control characters
  -v, --version               Print version and exit
  -H, --host HOST             Daemon socket to connect to

  --tls                       Use TLS; implied by --tlsverify
  --tlscacert CA_PATH         Trust certs signed only by this CA
  --tlscert CLIENT_CERT_PATH  Path to TLS certificate file
  --tlskey TLS_KEY_PATH       Path to TLS key file
  --tlsverify                 Use TLS and verify the remote
  --skip-hostname-check       Don't check the daemon's hostname against the
                              name specified in the client certificate
  --project-directory PATH    Specify an alternate working directory
                              (default: the path of the Compose file)
  --compatibility             If set, Compose will attempt to convert keys
                              in v3 files to their non-Swarm equivalent

Commands:
  build              Build or rebuild services
  bundle             Generate a Docker bundle from the Compose file
  config             Validate and view the Compose file
  create             Create services
  down               Stop and remove containers, networks, images, and volumes
  events             Receive real time events from containers
  exec               Execute a command in a running container
  help               Get help on a command
  images             List images
  kill               Kill containers
  logs               View output from containers
  pause              Pause services
  port               Print the public port for a port binding
  ps                 List containers
  pull               Pull service images
  push               Push service images
  restart            Restart services
  rm                 Remove stopped containers
  run                Run a one-off command
  scale              Set number of containers for a service
  start              Start services
  stop               Stop services
  top                Display the running processes
  unpause            Unpause services
  up                 Create and start containers
  version            Show the Docker-Compose version information
```

We can try `--help` option with `docker-compose` sub-commands like `build`, `create`, `bundle`, etc. The alone `help` option without `--` won't work.

```
$ docker-compose build --help
Build or rebuild services.

Services are built once and then tagged as `project_service`,
e.g. `composetest_db`. If you change a service's `Dockerfile` or the
contents of its build directory, you can run `docker-compose build` to rebuild it.

Usage: build [options] [--build-arg key=val...] [SERVICE...]

Options:
    --compress              Compress the build context using gzip.
    --force-rm              Always remove intermediate containers.
    --no-cache              Do not use cache when building the image.
    --pull                  Always attempt to pull a newer version of the image.
    -m, --memory MEM        Sets memory limit for the build container.
    --build-arg key=val     Set build-time variables for services.
    --parallel              Build images in parallel.


$ docker-compose create --help
Creates containers for a service.
This command is deprecated. Use the `up` command with `--no-start` instead.

Usage: create [options] [SERVICE...]

Options:
    --force-recreate       Recreate containers even if their configuration and
                           image haven't changed. Incompatible with --no-recreate.
    --no-recreate          If containers already exist, don't recreate them.
                           Incompatible with --force-recreate.
    --no-build             Don't build an image, even if it's missing.
    --build                Build images before creating containers.
```

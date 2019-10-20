## Lab 14

## `logs` command
The `docker-compose logs` command help to see the logs of all services defined in `docker-compose.yml` file. The logs of suppose say service 1 are displayed first followed by logs of service 2 and so on. They are not inter-mixed.

## Commands
```
docker-compose ps
docker-compose logs
docker-compose logs <service name>
docker-compose logs -f                  
docker-compose logs -f <service name>
docker-compose logs  --tail="2"  
docker-compose logs --tail="2" <service name>
docker-compose logs -f --tail="2"
docker-compose logs -f --tail="2" <service name>
```

* `docker-compose logs -f` will attach to log output where logs are populated in real time. Need to press CTRL+C to come out. This can result into mixed logs from all services.
* With `--tail="2"` option only the last 2 lins of log output will be displayed either for all services or only for specified services.
* A combination of `-f` and `--tail` options will display last specified no of log output and attach to real time log output.

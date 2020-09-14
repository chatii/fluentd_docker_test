# fluentd_docker_test

Fluentd and Docker with a local loopback address alias.

my env
- OS: macOS Catalina 10.15.6
- docker desktop: 2.3.0.4
- docker Engine: 19.03.12
- docker Compose: 1.26.2

## run

```shell script
sudo ifconfig lo0 alias 127.20.9.14 up
docker-compose up --build
```

## Problems

1. Logs of services (e.g. nginx) are not sent to Fluentd
2. Docker doesn't exit normally when `docker-compose stop` occurs (Docker for Mac needs to be restarted)

```
Stopping fluentd_docker_test_kibana_1        ... done
Stopping fluentd_docker_test_elasticsearch_1 ... done
Stopping fluentd_docker_test_nginx_1         ... 
Stopping fluentd_docker_test_fluentd_1       ... error

ERROR: for fluentd_docker_test_nginx_1  UnixHTTPConnectionPool(host='localhost', port=None): Read timed out. (read timeout=70)
ERROR: An HTTP request took too long to complete. Retry with --verbose to obtain debug information.
If you encounter this issue regularly because of slow network conditions, consider setting COMPOSE_HTTP_TIMEOUT to a higher value (current value: 60).
``` 

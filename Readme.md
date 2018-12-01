```
sudo mkdir -p /opt/osquery/logs
```

```
docker run \
    --rm \
    --name osquery \
    --net host \
    --privileged \
    -v /etc/passwd:/etc/passwd:ro \
    -v /var/log:/var/log:ro
    -e AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID \
    -e AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY \
    -e AWS_SESSION_TOKEN=$AWS_SESSION_TOKEN \
    -v /opt/osquery:/data \
    -t robertbeal/osquery \
    osqueryd \
    --config_path ./osquery.conf \
    --database_path ./db \
    --extensions_socket ./osquery.em \
    --pidfile process.pid \
    --logger_path ./logs \
    --verbose=true
```

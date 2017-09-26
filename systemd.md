# SystemD

Systemd is how we control what programs/services run on our linux computers.  The basic rundown is that you create `*.service` files, load them into the systemctl daemon and then configure then for start on bootup or manually start them.

## Places

`/etc/systemd/system/SERVICE_NAME.service`

## Service File Format

```
[Unit]
Description=A silly phrase
After=docker.service  # Specify services to wait before trying to start
Requires=docker.service  # Specifies what other services this unit requires installed

[Service]
TimeoutStartSec=0
ExecStartPre=-/cmd/to/run/before/service/start
ExecStartPre=-/usr/bin/docker kill %p
ExecStartPre=-/usr/bin/docker rm %p
ExecStart=/usr/bin/docker run --name %p busybox /bin/sh -c "echo hello"

[Install]
WantedBy=multi-user.target
```

## Commands

###### List ALL services
- `systemctl list-units`

###### Show details on a service
- `systemctl show service_name.service`

###### Enable a newly created service
- `systemctl enable /etc/systmd/system/service_name.service`

###### Reload the services in systemd to reflect recent changes
- `systemctl daemon-reload`

###### Start/ Restart/ Stop a service
- `systemctl start/ restart/ stop service_name.service`

###### Display STDOUT logs from service
- `journalctl -f -u service_name.service`

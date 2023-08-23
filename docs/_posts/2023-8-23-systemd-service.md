---
title: "Manage your own daemon! - Systemd services"
author: "Samuel Kriikkula"
---

Hello there! It's Samuel back in the game. Today I will teach you about daemons and systemd Services.

## What the heck is a daemon?
In Linux, daemons are programs that run silently in the background. They provide services such as audio, video, networking, databases, docker containers, and much more. They can also be for example python scripts, or game servers if you like.

## What is Systemd?
![Systemd Logo](https://en.wikipedia.org/wiki/Systemd#/media/File:Systemd-logo.svg)
Systemd is an init service. When the kernel is loaded, the init system takes control.
I'm not going deeper this time, the only necessary thing here is the fact that Systemd manages the daemons of your system.

## Our simple webserver
Let's code a simple hello world webpage.
Save it to `/opt/web-daemon.py` or anywhere of your liking.
This python code will do:
```python
import http.server
import socketserver
from http import HTTPStatus

class Handler(http.server.SimpleHTTPRequestHandler):
    def do_GET(self):
        self.send_response(HTTPStatus.OK)
        self.end_headers()
        self.wfile.write(b'Hello world')


httpd = socketserver.TCPServer(('', 8000), Handler)
httpd.serve_forever()
```

## Let's make a daemon
**Note!** The process is a bit different for some distributions

Locate to this directory: `/etc/systemd/system`. Our daemons live here!

Let's define a daemon.
For example `web-daemon.service`
```ini
[Service]
WorkingDirectory=/opt
ExecStart=python3 /opt/web-daemon.py

[Install]
WantedBy=multi-user.target
```

That's it!

## Starting and enabling
These commands manage your daemon:
```
sudo systemctl start web-daemon   # Start the daemon
sudo systemctl stop web-daemon    # Stop the daemon
sudo systemctl status web-daemon  # Show the status of the process
sudo systemctl enable web-daemon  # Enable the daemon to start on system startup
sudo systemctl disable web-daemon # You get the drill
```
## Finishing up
Start the daemon and naviage to localhost:8000 and you should see a friendy message.

See you in the next one ;)

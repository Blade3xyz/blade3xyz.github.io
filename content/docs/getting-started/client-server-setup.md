---
title: "Client/Server Setup"
description: "Guided installation for all platforms"
summary: "Install blade3 on Linux, Mac, Windows, and FreeBSD"
draft: false
weight: 30
toc: false
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  robots: "" # custom robot tags (optional)
---

Setup the Blade3 client, and server.

## Client vs Server
If you're confused about which machine is the client, and which is the server, then consult the diagram below.

![](/images/blade3diagram.png)

### Encryption setup
When each program starts it will check for an encryption key at ```/etc/blade3/crypto/blade3.key```. If it does not exist it will generate one. In order for Blade3 to work both servers **MUST** share the same key, if you have SSH configured you can copy it with ```scp```.

### Server Setup
The blade3 server runs on the non-firewall protected server.

#### Systemd autostart (Optional)
If you want the Blade3 server to start on boot we can create a systemd service for it. Note that if you are running on a system which does not use systemd(Gentoo, MacOS, Artix, etc) this will not work.

First create a file at ```/etc/systemd/system/blade3server.service```, and put the following content in it

```systemd
[Unit]
Description=Blade3 remote server

[Service]
Type=simple
ExecStart=/usr/bin/blade3-server

[Install]
WantedBy=multi-user.target
```
Now you can use the following commands to start, and add it.

```bash
# Update permissions for the blade3 server
sudo chmod 640 /etc/systemd/system/blade3server.service

# Reload the systemd daemon
sudo systemctl daemon-reload

# Enable the blade3 service
sudo systemctl enable blade3server

# (Optional) Start the blade3 server right now
sudo systemctl start blade3server
```

#### Server configuration
The server configuration can be found at ```/etc/blade3/server_config.rb```. If you don't know ruby thats 100% ok. The config file is easy to understand, and modify. You will most likely never touch the server config file, as the port and address usually stay the same.

#### Running manually (without systemd)
After you have changed the config file(if you want) you can start the server. The server can be started by using the ```blade3-server``` command, or by calling ```ruby /usr/lib/blade3/blade3_server.rb```

### Client Setup
The blade3 client runs on the firewall protected server.

#### Systemd autostart (Optional)
If you want the Blade3 client to start on boot we can create a systemd service for it. Note that if you are running on a system which does not use systemd(Gentoo, MacOS, Artix, etc) this will not work.

First create a file at ```/etc/systemd/system/blade3client.service```, and put the following content in it

```systemd
[Unit]
Description=Blade3 client service

[Service]
Type=simple
ExecStart=/usr/bin/blade3-client

[Install]
WantedBy=multi-user.target
```
Now you can use the following commands to start, and add it.

```bash
# Update permissions for the blade3 server
sudo chmod 640 /etc/systemd/system/blade3client.service

# Reload the systemd daemon
sudo systemctl daemon-reload

# Enable the blade3 service
sudo systemctl enable blade3client

# (Optional) Start the blade3 client right now
sudo systemctl start blade3client
```

#### Client configuration
The server configuration can be found at ```/etc/blade3/client_config.rb```. If you don't know ruby thats 100% ok. The config file is easy to understand, and modify. For more information see the [Client config reference]()

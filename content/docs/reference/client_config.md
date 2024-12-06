---
title: "Client config"
description: "Client configuration reference"
summary: ""
draft: false
weight: 910
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  robots: "" # custom robot tags (optional)
---

The client config is located at ```/etc/blade3/client_config.rb```

## Default config
```ruby
class ClientConfig
  # Return ports to forward, and their remote mapping
  def get_ports()
    return [
      {
        client_port: 8000,
        remote_port: 8090
      },
      {
        client_port: 25565,
        remote_port: 25568
      }
    ]
  end

  # Get the client remote server address
  def get_remote_address()
    return "0.0.0.0" # CHANGE THIS!!!
  end

  # Get the cleint remote server port
  def get_remote_port()
    return 9743
  end
end
```

### Changing the remote server address
By default the remote server address is ```0.0.0.0```, you need to change this, otherwise the remote server is going to be your local machine. Change the value in quotations marks to the remote server's public IP address

### Forwarding ports
The ```get_ports``` function returns a list of ruby ```Hash```s, in order to add a new port we can add a new Hash instance to the returned array. See below for an example
```ruby
  def get_ports()
    return [
      {
        client_port: 8000,
        remote_port: 8090
      },
      {
        client_port: 25565,
        remote_port: 25568
      },
      # !!! New text begins here !!!
      {
        client_port: 8080 # The port of the service on the local machine
        remote_port: 8090 # The port of the service on the remote machine
      }
      # !!! New text ends here !!!
    ]
  end
```

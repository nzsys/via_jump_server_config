# via_jump_server
SSH connection via jump server for mac.

### case .ssh/config
```sh
Host jumpServer
  HostName {jumpServerHostName}
  User {jumpServerUser}
  # When specifying a public key in the .ssh directory
  # IdentityFile 

Host targetServer
  HostName {targetServerHostName}
  User {targetServerUser}
  ProxyCommand ssh -W %h:%p jumpServer
```
#### connect
```sh
ssh targetServer
```

### case port forwarding
```sh
ssh -N -f -L {anyPort}:{targetServerHostName}:{targetServerPort} {jumpServerUser}@{jumpServerHost} -p {jumpServerPort}
```
#### connect
```sh
ssh targetServerUser@localhost:{anyPort}
```

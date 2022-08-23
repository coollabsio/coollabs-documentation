# Remote Docker Engine
Allows you to use any kind of server as a destination endpoint.

You can have one Coolify instance as a control-plane/dashboard and deploy to unlimited number of remote servers.

### Requirements
The server needs to have:
1. Install Docker Engine (20.11+) - [instructions](https://docs.docker.com/engine/install/).
2. Add SSH public key to `.ssh/authorized_keys` file in the proper user's home directory - recommended root.
3. Add the **private key** of the same SSH key added to the remote server in the `Settings/SSH Keys` menu.

# AltManager Docker Deploy

Deploys the AltManager backend server and web frontend using Docker Compose.

## Installing

```sh
git clone https://github.com/altmanager/docker-deploy.git altmanager
cd altmanager
docker compose up -d
```

## Configuration

> [!IMPORTANT]
> If your altmanager-ws backend server is publicly accessible, anyone can connect/disconnect your accounts or add new accounts. Consider setting up a reverse proxy with authentication or VPN to restrict access.
>
> The frontend is safe to be exposed publicly. It will display an error if it cannot connect to the backend.

You can configure the ports in use in the `compose.yaml` file. The following environment variables can also be configured.

## altmanager-web

<dl>
  <dt>ALTMANAGER_SERVER</dt>
  <dd>The websocket connection URI to the backend server. Should include the <code>ws://</code> or <code>wss://</code> protocol. The default is <code>ws://localhost:14454</code>.</dd>
</dl>

The environment variables are exposed to the frontend service via an [Nginx substitution template](https://github.com/altmanager/altmanager-web/blob/main/env.json.template). Nginx serves them as an `env.json` file. The frontend performs a `GET /env.json` to read them.

Modifying the environment variables requires the frontend container to be restarted for them to take effect.


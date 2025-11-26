# n8n-docker-setup
A basic docker compose to scuffold n8n projects

- **Purpose**: Run n8n with Postgres and persistent volumes using Docker Compose.
- **Files**: `docker-compose.yml`, `.env`.

**Quick Start**

1. Copy and edit the `.env` file to choose secure passwords and settings.

2. Start the stack:

```zsh
docker compose up -d
```

3. Open n8n in your browser at `http://localhost:5678` (or the host you set in `.env`).

4. To stop the stack:

```zsh
docker compose down
```

**Notes & Recommendations**

- **Secure secrets**: Replace `POSTGRES_PASSWORD` and `N8N_BASIC_AUTH_PASSWORD` with strong values before exposing to the internet.
- **Production**: Run behind a reverse proxy (Traefik/Caddy/Nginx) with TLS. Set `N8N_PROTOCOL=https` and `WEBHOOK_TUNNEL_URL` to your external URL when behind a proxy.
- **Backups**: Postgres data is persisted in the `postgres_data` volume; back it up regularly.

If you want, I can also:
- Add a Traefik example for TLS and Let’s Encrypt.
- Add Redis or n8n worker services for scaling.

If you are running **ollama** locally on port 11434 (default) use the following base url as the credentials for the n8n ollama node:
  ```zsh
  http://host.docker.internal:11434
  ```

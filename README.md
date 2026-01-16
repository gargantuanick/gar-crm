# Gargantua LLC CRM

Self-hosted [Twenty CRM](https://twenty.com) for Gargantua LLC.

**Production URL**: `https://crm.gargantua.llc`

## Quick Start (Local Development)

```bash
# 1. Copy environment file
cp .env.example .env

# 2. Edit .env with your settings (see Configuration below)

# 3. Start the CRM
docker compose up -d

# 4. Access at http://localhost:3000
```

## Configuration

### Required Environment Variables

Edit `.env` with your values:

| Variable | Description |
|----------|-------------|
| `APP_SECRET` | Generate with `openssl rand -base64 32` |
| `PG_DATABASE_PASSWORD` | Strong password (no special chars) |
| `SERVER_URL` | `http://localhost:3000` (dev) or `https://crm.gargantua.llc` (prod) |

### Google OAuth (GSuite Login)

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create project: "Gargantua CRM"
3. Enable APIs: Gmail, Google Calendar, People
4. Create OAuth 2.0 credentials
5. Add redirect URIs:
   - `https://crm.gargantua.llc/auth/google/redirect`
   - `https://crm.gargantua.llc/auth/google-apis/get-access-token`
6. Update `.env`:
   ```
   AUTH_GOOGLE_CLIENT_ID=your_client_id
   AUTH_GOOGLE_CLIENT_SECRET=your_client_secret
   ```

## Commands

```bash
# Start
docker compose up -d

# Stop
docker compose down

# View logs
docker compose logs -f

# Restart
docker compose restart
```

## Deploy to Render

1. Connect this repo to Render
2. Set environment variables in Render dashboard
3. Point `crm.gargantua.llc` DNS to Render

## Resources

- [Twenty Documentation](https://twenty.com/developers)
- [Self-Hosting Guide](https://twenty.com/developers/self-host/self-host)

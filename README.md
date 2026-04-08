# Horilla HRMS - One Click Deploy

Deploy your own Horilla HRMS instance on Railway in seconds.

## Features

- ✅ Free and Open Source HRMS
- ✅ PostgreSQL Database with persistent storage
- ✅ Auto-configured with all migrations
- ✅ Gettext support for multi-language
- ✅ Static files and message compilation included
- ✅ CSRF protection configured
- ✅ Database auto-initialization

## Deploy Now

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/new?templateUrl=https://github.com/vizsoftglobal/horilla-saas-template)

## What Gets Deployed

### Horilla Service
- Image: `horilla/horilla:1.4`
- Gunicorn WSGI server on port 8000
- Auto-runs migrations on startup
- Collects static files
- Compiles message files for multi-language support
- Installs gettext for message compilation

### PostgreSQL Database
- Image: `postgres:16-bullseye`
- Persistent volume for data
- Auto-initialized with `horilla` database
- Health checks enabled
- Secure password auto-generated

## After Deployment

1. Wait 2-3 minutes for services to start
2. Access your Horilla instance at the public domain (shown in Railway dashboard)
3. Click "Initialize Database"
4. Enter the PostgreSQL password (shown in Postgres service variables)
5. Create your admin username and password
6. Log in and start using Horilla!

## Environment Variables

| Variable | Value | Purpose |
|----------|-------|---------|
| `DATABASE_URL` | Auto-connected | PostgreSQL connection string |
| `ALLOWED_HOSTS` | `*` | Accept requests from any host |
| `CSRF_TRUSTED_ORIGINS` | Auto-set | CSRF protection for your domain |
| `DB_INIT_PASSWORD` | Auto-set | Database password for initialization |
| `POSTGRES_PASSWORD` | Auto-generated | PostgreSQL admin password |

## Custom Domain Setup

To add a custom domain after deployment:
1. Go to your Horilla service in Railway
2. Add a custom domain
3. Update your DNS provider (Cloudflare, etc.) with a CNAME record pointing to your Railway domain
4. Update `CSRF_TRUSTED_ORIGINS` in Horilla service variables to include your custom domain

## Troubleshooting

### Service won't start?
- Check Railway logs for errors
- Wait for PostgreSQL to be ready (healthcheck)

### Database connection failed?
- Ensure PostgreSQL service is running
- Check POSTGRES_PASSWORD in Postgres service variables

### Static files not loading?
- They're auto-collected on startup
- Check deploy logs for collectstatic errors

### CSRF errors?
- CSRF_TRUSTED_ORIGINS is auto-configured
- For custom domains, add them to CSRF_TRUSTED_ORIGINS
- Clear browser cache and try again

## Support

- **Horilla Documentation**: https://horilla.readthedocs.io/
- **Railway Docs**: https://docs.railway.app/
- **GitHub Issues**: https://github.com/horilla-opensource/horilla/issues

## License

Horilla is open source. See the [Horilla repository](https://github.com/horilla-opensource/horilla) for license details.

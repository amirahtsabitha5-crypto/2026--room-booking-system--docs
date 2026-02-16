# Room Booking System - Infrastructure Configuration

This directory contains all infrastructure-related configuration files for the Room Booking System.

## Files

### Environment Files

- **`.env`** - Production/Local environment variables (DO NOT commit to repo)
- **`.env.example`** - Example environment variables template (safe to commit)

### Docker Files

#### docker/docker-compose.yml
Complete Docker Compose setup with:
- PostgreSQL database service
- Backend API service (.NET)
- Frontend service (React)
- Network and volume configuration
- Health checks

#### docker/Dockerfile.backend
Docker image for the .NET backend API
- Multi-stage build for optimized image size
- Builds in Release configuration
- Exposes port 5000

#### docker/Dockerfile.frontend
Docker image for React frontend
- Node.js builder image
- Optimized production build
- Uses `serve` to run static files
- Exposes port 3000

## Getting Started

### 1. Setup Environment Variables

Copy the example file to create your local environment:

```bash
cp infrastructure/.env.example infrastructure/.env
```

Edit `infrastructure/.env` and update the variables:

- `DB_PASSWORD` - PostgreSQL password
- `JWT_SECRET` - Generate a strong secret key
- `API_URL` - Backend API endpoint
- `CORS_ORIGINS` - Allowed origins for CORS

### 2. Build and Run with Docker

From the root directory:

```bash
# Build all images
docker-compose -f infrastructure/docker/docker-compose.yml build

# Start all services
docker-compose -f infrastructure/docker/docker-compose.yml up -d

# View logs
docker-compose -f infrastructure/docker/docker-compose.yml logs -f

# Stop all services
docker-compose -f infrastructure/docker/docker-compose.yml down
```

### 3. Access Services

- **Backend API**: http://localhost:5000
- **Frontend**: http://localhost:3000
- **PostgreSQL**: localhost:5432

## Services

### PostgreSQL Database
- Container: `room_booking_postgres`
- Port: 5432
- Database: room_booking_db
- Username: postgres
- Volume: `postgres_data` (persistent)

### Backend API
- Container: `room_booking_backend`
- Port: 5000
- Health Check: Enabled
- Depends on: PostgreSQL

### Frontend
- Container: `room_booking_frontend`
- Port: 3000
- Depends on: Backend

## Development vs Production

### Development (.env)
```
ASPNETCORE_ENVIRONMENT=Development
LOG_LEVEL=Information
REACT_APP_ENV=development
```

### Production
Update `.env` to:
```
ASPNETCORE_ENVIRONMENT=Production
LOG_LEVEL=Warning
REACT_APP_ENV=production
```

## Troubleshooting

### Database connection issues
- Ensure PostgreSQL container is running: `docker ps`
- Check logs: `docker-compose logs postgres`
- Verify connection string in `.env`

### Port already in use
If ports are in use, modify in `.env`:
- Change `APP_PORT` for backend
- Modify frontend port in service

### Docker daemon not running
Ensure Docker Desktop is running or Docker daemon is started

## Security Notes

⚠️ **IMPORTANT:**
- Never commit `.env` file to version control
- Use `.env.example` as template with placeholder values
- Rotate JWT_SECRET regularly in production
- Use strong database passwords
- Keep environment variables secret

## More Information

See root [README.md](../README.md) for complete project documentation.

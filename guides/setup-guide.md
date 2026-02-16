# Room Booking System - Setup Guide

## Prerequisites

### System Requirements
- Windows 10/11, macOS 10.15+, or Linux (Ubuntu 20.04+)
- Git installed
- Docker & Docker Compose (for containerized setup)

### Software Requirements

**Backend (.NET)**
- .NET 10 SDK
- PostgreSQL 14+
- Visual Studio 2022 or VS Code with C# extension

**Frontend (React)**
- Node.js 18+
- npm or yarn

**Mobile**
- Android Studio (for Android development)
- Xcode (for iOS development)

## Backend Setup

### 1. Navigate to backend directory
```bash
cd backend
```

### 2. Install dependencies
```bash
dotnet restore
```

### 3. Setup Database

Update `appsettings.Development.json`:
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Host=localhost;Port=5432;Database=room_booking;Username=postgres;Password=yourpassword"
  }
}
```

### 4. Run migrations
```bash
dotnet ef database update
```

### 5. Start the backend server
```bash
dotnet run
```

Server akan berjalan di `http://localhost:5000`

## Frontend Setup

### 1. Navigate to frontend directory
```bash
cd frontend
```

### 2. Install dependencies
```bash
npm install
```

### 3. Create .env file
```
VITE_API_URL=http://localhost:5000/api
```

### 4. Start development server
```bash
npm run dev
```

Application akan berjalan di `http://localhost:5173`

## Docker Setup

### Using Docker Compose

```bash
# From project root
docker-compose up -d
```

This will start:
- PostgreSQL (port 5432)
- Backend API (port 5000)
- Frontend (port 80)

### Build custom images

```bash
# Backend
docker build -f backend/Dockerfile -t room-booking-backend:latest ./backend

# Frontend
docker build -f frontend/Dockerfile -t room-booking-frontend:latest ./frontend
```

## Mobile Setup

### Android
```bash
cd mobile/android
# Open in Android Studio and run on emulator/device
```

### iOS
```bash
cd mobile/ios
pod install
# Open in Xcode and run on simulator/device
```

## Database Connection

### PostgreSQL Setup

```bash
# Using Docker
docker run --name postgres-room-booking \
  -e POSTGRES_PASSWORD=yourpassword \
  -e POSTGRES_DB=room_booking \
  -p 5432:5432 \
  -d postgres:14

# Using local PostgreSQL
createdb room_booking
```

## Verification

### Check Backend
```bash
curl http://localhost:5000/api/rooms
```

### Check Frontend
Open browser and navigate to `http://localhost:5173`

### Check Database
```bash
psql -h localhost -U postgres -d room_booking
# List tables: \dt
# Exit: \q
```

## Troubleshooting

### Port already in use
```bash
# Find process using port 5000
lsof -i :5000
# or
netstat -ano | findstr :5000

# Kill the process
kill -9 <PID>  # Linux/Mac
taskkill /PID <PID> /F  # Windows
```

### Database connection error
- Verify PostgreSQL is running
- Check connection string in `appsettings.json`
- Ensure database exists

### Node modules issues
```bash
rm -rf node_modules package-lock.json
npm install
```

## Next Steps

1. Read [Development Guide](development-guide.md)
2. Check [API Documentation](../api)
3. Review [Architecture Overview](../architecture/architecture-overview.md)

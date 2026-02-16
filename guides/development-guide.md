# Room Booking System - Development Guide

## Project Structure

```
room-booking-system/
├── backend/              # .NET Core API
│   ├── Controllers/      # API endpoints
│   ├── Services/         # Business logic
│   ├── Models/           # Data models
│   ├── Migrations/       # Database migrations
│   └── Program.cs        # Entry point
├── frontend/             # React web application
│   ├── src/
│   │   ├── components/   # React components
│   │   ├── services/     # API services
│   │   └── types/        # TypeScript types
│   └── index.html        # Entry HTML
├── mobile/               # Mobile applications
│   ├── android/          # Android app
│   ├── ios/              # iOS app
│   └── shared/           # Shared code
├── doc/                  # Documentation
└── infrastructure/       # Deployment configs
```

## Code Style Guidelines

### C# (.NET Backend)

```csharp
// Class naming: PascalCase
public class BookingService
{
    // Methods: PascalCase
    public async Task<BookingDto> CreateBooking(CreateBookingRequest request)
    {
        // Implementation
    }

    // Private methods: camelCase
    private bool ValidateBooking(Booking booking)
    {
        // Implementation
    }
}

// Interfaces: IPascalCase
public interface IBookingRepository
{
    // Methods
}

// Variables: camelCase
var bookingId = "123";
```

### TypeScript/React (Frontend)

```typescript
// Component naming: PascalCase
export function BookingForm(): JSX.Element {
  // Implementation
}

// Variables: camelCase
const bookingData = {};

// Constants: UPPER_SNAKE_CASE
const MAX_BOOKING_DAYS = 30;

// Interfaces: PascalCase
interface IBooking {
  id: string;
  roomId: string;
  startTime: Date;
  endTime: Date;
}
```

## Development Workflow

### 1. Create a Feature Branch
```bash
git checkout -b feature/room-search
```

### 2. Make Changes
- Commit frequently with meaningful messages
```bash
git commit -m "feat: add room search functionality"
```

### 3. Test Locally
```bash
# Backend
cd backend && dotnet test

# Frontend
cd frontend && npm test
```

### 4. Push and Create Pull Request
```bash
git push origin feature/room-search
```

## Adding New Features

### Frontend: Add a React Component

1. Create component file in `src/components/`
```typescript
// FeatureName.tsx
import React from 'react';

interface Props {
  // Props definition
}

export const FeatureName: React.FC<Props> = (props) => {
  return (
    <div>
      {/* Component JSX */}
    </div>
  );
};
```

2. Update `src/components/App.tsx` to include the component

### Backend: Add a New API Endpoint

1. Add model in `Models/`
```csharp
public class NewModel
{
    public string Id { get; set; }
    // Properties
}
```

2. Create DTO in `DTOs/`
```csharp
public class NewModelDto
{
    public string Id { get; set; }
    // Properties
}
```

3. Add controller in `Controllers/`
```csharp
[ApiController]
[Route("api/[controller]")]
public class NewController : ControllerBase
{
    [HttpGet]
    public async Task<ActionResult<IEnumerable<NewModelDto>>> Get()
    {
        // Implementation
    }
}
```

4. Run migrations if database schema changed
```bash
dotnet ef migrations add NewModelMigration
dotnet ef database update
```

### Database: Add a Migration

```bash
cd backend
dotnet ef migrations add MigrationName
dotnet ef database update
```

## Testing

### Backend Tests
```bash
cd backend
dotnet test

# Run specific test file
dotnet test --filter "TestClassName"
```

### Frontend Tests
```bash
cd frontend
npm test

# Run with coverage
npm test -- --coverage
```

## Debugging

### Flask Backend Debugging
```csharp
// Add breakpoints in Visual Studio
// Or use Debug Logging
logger.LogDebug("Debug message: {value}", value);
```

### React Frontend Debugging
```typescript
// Browser DevTools (F12)
// React DevTools extension
console.log("Debug info:", data);
```

## Performance Optimization

### Backend
- Use async/await for I/O operations
- Implement database query optimization
- Add caching for frequently accessed data

### Frontend
- Code splitting with React.lazy()
- Image optimization
- Minimize bundle size

## Database Queries

### Query Examples

**Get all rooms:**
```csharp
var rooms = await _context.Rooms.ToListAsync();
```

**Get bookings for a specific room:**
```csharp
var bookings = await _context.Bookings
    .Where(b => b.RoomId == roomId)
    .ToListAsync();
```

**Complex query with joins:**
```csharp
var bookingsWithRooms = await _context.Bookings
    .Include(b => b.Room)
    .Where(b => b.StartTime >= DateTime.Now)
    .OrderBy(b => b.StartTime)
    .ToListAsync();
```

## Common Issues

### Issue: Changes not reflecting
- Clear cache: `npm cache clean --force` (Frontend)
- Rebuild: `dotnet clean && dotnet build` (Backend)
- Hard refresh browser: Ctrl+Shift+R

### Issue: Database errors
- Check connections string in appsettings
- Ensure migrations are up to date
- Verify PostgreSQL is running

## Resources

- [Microsoft .NET Documentation](https://docs.microsoft.com/dotnet/)
- [React Documentation](https://react.dev/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)

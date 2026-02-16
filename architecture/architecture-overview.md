# Room Booking System - Architecture Overview

## System Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Frontend Layer                       │
├─────────────────────────────────────────────────────────┤
│  Web (React + TypeScript)  │  Mobile (React Native)     │
│  - Book Rooms              │  - iOS (Swift)             │
│  - View Availability       │  - Android (Kotlin/Java)   │
│  - Booking History         │  - Shared Components       │
└────────────────┬──────────────────────────┬─────────────┘
                 │                          │
                 └──────────────┬───────────┘
                                │
                   ┌─────────────▼───────────┐
                   │   API Gateway/Load     │
                   │    Balancer            │
                   └─────────────┬───────────┘
                                │
                ┌───────────────┴───────────────┐
                │                               │
┌───────────────▼──────────────────┐  ┌─────────▼─────────────┐
│   Backend API Layer (.NET)       │  │  Cache Layer (Redis)  │
├──────────────────────────────────┤  └───────────────────────┘
│ - Controllers (REST API)         │
│ - Services (Business Logic)      │
│ - Data Access (Entity Framework) │
└───────────────┬──────────────────┘
                │
                │
    ┌───────────▼───────────┐
    │  Database Layer       │
    ├───────────────────────┤
    │ - PostgreSQL          │
    │ - Tables: Rooms,      │
    │   Bookings,           │
    │   StatusHistory       │
    └───────────────────────┘
```

## Technology Stack

### Frontend
- **Web**: React 18, TypeScript, Vite
- **Mobile**: React Native / Native (iOS Swift, Android Kotlin)
- **State Management**: Context API / Redux
- **HTTP Client**: Axios / Fetch API

### Backend
- **Runtime**: .NET 10
- **Framework**: ASP.NET Core
- **ORM**: Entity Framework Core
- **Database**: PostgreSQL
- **API**: RESTful API

### Infrastructure
- **Containerization**: Docker
- **Orchestration**: Kubernetes (optional)
- **Infrastructure as Code**: Terraform
- **CI/CD**: GitHub Actions

## Key Components

### Backend Services

1. **RoomsController** - Manage room data
2. **BookingsController** - Handle booking operations
3. **BookingRepository** - Data access pattern
4. **ApplicationDbContext** - EF Core context

### Data Models

- **Room** - Store room information
- **Booking** - Store booking records
- **StatusHistory** - Track booking status changes

### Frontend Components

- **RoomList** - Display available rooms
- **BookingForm** - Create new bookings
- **BookingDetail** - View booking details
- **BookingHistory** - Track booking changes

## Database Schema

```
┌──────────────┐      ┌──────────────┐
│    Rooms     │      │   Bookings   │
├──────────────┤      ├──────────────┤
│ id (PK)      │◄─────│ id (PK)      │
│ name         │      │ roomId (FK)  │
│ capacity     │      │ startTime    │
│ location     │      │ endTime      │
│ amenities    │      │ bookedBy     │
│ status       │      │ status       │
│ createdAt    │      │ createdAt    │
│ updatedAt    │      │ updatedAt    │
└──────────────┘      └──────┬───────┘
                             │
                        ┌────▼──────────────┐
                        │ StatusHistory     │
                        ├─────────────────  │
                        │ id (PK)           │
                        │ bookingId (FK)    │
                        │ status            │
                        │ changedAt         │
                        │ remarks           │
                        └───────────────────┘
```

## Deployment Strategy

1. **Development**: Local setup with Docker Compose
2. **Staging**: Kubernetes cluster with staging configurations
3. **Production**: Kubernetes cluster with auto-scaling

## Security Considerations

- Input validation on all endpoints
- CORS configuration for frontend
- Database connection pooling
- Rate limiting (future enhancement)
- Authentication & Authorization (future enhancement)

## Scalability

- Database indexing on frequently queried fields
- Caching layer for room data
- API rate limiting per user/IP
- Horizontal scaling with Kubernetes

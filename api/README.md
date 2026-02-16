# Room Booking System - API Documentation

## Base URL

```
http://localhost:5000/api
```

## Authentication

Saat ini API bersifat public (tanpa authentication).

## Endpoints

### Rooms

#### Get All Rooms
```
GET /api/rooms
```

Response:
```json
{
  "data": [
    {
      "id": "1",
      "name": "Conference Room A",
      "capacity": 10,
      "location": "Floor 2",
      "amenities": ["Projector", "Whiteboard"],
      "status": "available"
    }
  ],
  "success": true
}
```

#### Get Room by ID
```
GET /api/rooms/{id}
```

### Bookings

#### Get All Bookings
```
GET /api/bookings
```

#### Create Booking
```
POST /api/bookings
Content-Type: application/json

{
  "roomId": "1",
  "startTime": "2026-02-16T10:00:00Z",
  "endTime": "2026-02-16T11:00:00Z",
  "bookedBy": "user@example.com"
}
```

#### Get Booking by ID
```
GET /api/bookings/{id}
```

#### Update Booking
```
PUT /api/bookings/{id}
Content-Type: application/json

{
  "startTime": "2026-02-16T10:30:00Z",
  "endTime": "2026-02-16T11:30:00Z"
}
```

#### Cancel Booking
```
DELETE /api/bookings/{id}
```

#### Get Booking History
```
GET /api/bookings/{id}/history
```

## Error Responses

```json
{
  "success": false,
  "message": "Error description"
}
```

## Status Codes

- `200 OK` - Request successful
- `201 Created` - Resource created
- `400 Bad Request` - Invalid request
- `404 Not Found` - Resource not found
- `500 Internal Server Error` - Server error

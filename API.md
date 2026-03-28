# VoyageIQ — API Contract
# Backend builds these. Frontend calls these.

Base URL (dev):   http://localhost:4000/api
Base URL (prod):  https://voyageiq-api.onrender.com/api

## Auth
POST /api/auth/register
  Body:    { name, email, password }
  Returns: { token, user: { id, name, email } }

POST /api/auth/login
  Body:    { email, password }
  Returns: { token, user: { id, name, email } }

## Flights
GET /api/flights/search?from=JFK&to=LAX&date=2026-07-01
  Returns: { flights: Flight[] }

## Budget
POST /api/budget/calculate
  Body:    { destination, startDate, endDate, totalBudget, groupSize }
  Returns: { breakdown: BudgetBreakdown }

## Trips
GET    /api/trips          → list all trips for logged-in user
POST   /api/trips          → create a new trip
GET    /api/trips/:id      → get one trip
PUT    /api/trips/:id      → update a trip
DELETE /api/trips/:id      → delete a trip

## Error format
All errors: { error: "message" }
Codes: 400 bad input | 401 unauthorized | 404 not found | 500 server error

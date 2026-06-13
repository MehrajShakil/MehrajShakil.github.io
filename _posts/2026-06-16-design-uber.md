---
title: "Design Uber"
date: 2026-06-16
topic: system-design-problems
order: 1
tags: [system-design, uber, geospatial]
---

Kicking off the **System Design Problems** series with a big one: designing a
ride-hailing service like **Uber**. We'll follow the same five-step framework —
requirements, scale, API, high-level design, and deep dives.

## 1. Requirements

**Functional**

- Riders can request a ride from A to B.
- Match a rider with a nearby available driver.
- Track driver/rider location in real time during a trip.
- Fare calculation and payment.

**Non-functional**

- Low latency matching (seconds, not minutes).
- High availability — the service can't go down.
- Consistency of trip state; eventual consistency is fine for location pings.

## 2. Scale estimate

- Tens of millions of daily active users.
- Millions of concurrent drivers sending location updates every ~4 seconds.
- Read/write heavy on location data.

## 3. API (sketch)

```
POST /rides/request      { riderId, pickup, dropoff } -> { rideId, status }
POST /drivers/location   { driverId, lat, lng }        -> 200
GET  /rides/{id}                                        -> { status, driver, eta }
```

## 4. High-level design

- **Location service:** ingests driver pings; stores current positions.
- **Matching service:** finds nearby drivers for a request.
- **Trip service:** owns trip lifecycle (requested → matched → ongoing → completed).
- **Notification / WebSocket gateway:** pushes real-time updates to apps.
- **Payment service:** fare + charge after completion.

## 5. Deep dives & trade-offs

### Geospatial indexing

The core challenge is "find drivers near this point" fast. Options:

- **Geohash** buckets — group the map into cells; query the rider's cell + neighbors.
- **QuadTree** — adaptively subdivide dense areas.
- **S2 / H3** cells — production-grade hierarchical geospatial indexing.

### Handling location updates at scale

- Use a fast in-memory store (e.g. Redis) keyed by geohash for current positions.
- Batch/throttle pings; don't persist every update to the primary DB.

### Matching strategy

- Query candidate drivers in nearby cells, rank by ETA, dispatch, handle declines.

> Next in this series: **Design Netflix** — video streaming at scale.

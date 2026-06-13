---
title: "System Design Problem: Design a URL Shortener"
date: 2026-06-15
topic: system-design
order: 2
tags: [system-design, problem]
---

Time to apply [the framework](/articles/2026/06/14/system-design-how-to-approach-any-problem/)
to a classic problem: a URL shortener like TinyURL.

## Requirements

- **Functional:** shorten a long URL; redirect a short URL to the original.
- **Non-functional:** highly available, low-latency redirects, read-heavy.

## Scale estimate

Assume 100M new URLs/month and a 100:1 read-to-write ratio.

## API

```
POST /shorten   { url }      -> { shortUrl }
GET  /{code}                 -> 301 redirect
```

## Core idea

Generate a unique short **code** (base62 of an ID or a hash) and store the
mapping `code -> long URL` in a fast key-value store, fronted by a cache.

## Trade-offs

- Counter/ID generation vs. hashing (collision handling).
- Cache strategy for hot links.
- Custom aliases and expiry.

> Next: we'll tackle designing a rate limiter.

---
title: "System Design: How to Approach Any Problem"
date: 2026-06-14
topic: system-design
order: 1
tags: [system-design, fundamentals]
---

Welcome to my **System Design** series. I'm using this space to think out loud —
working through concepts and classic problems one step at a time, in order.

This first post lays out the framework I use for *every* design problem.

## 1. Clarify requirements

- **Functional:** what must the system do?
- **Non-functional:** scale, latency, availability, consistency.
- Always ask before assuming.

## 2. Estimate scale

Back-of-the-envelope numbers: users, QPS, storage, bandwidth.

## 3. Define the API

A small, clear interface forces you to nail down what the system actually does.

## 4. High-level design

Draw the boxes: clients, load balancer, services, databases, caches, queues.

## 5. Deep dive & trade-offs

Pick the interesting parts and discuss the trade-offs — there's rarely one right answer.

> Next up, we'll apply this framework to a real problem: designing a URL shortener.

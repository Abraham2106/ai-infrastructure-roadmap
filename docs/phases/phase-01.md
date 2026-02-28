# Phase 1 — Foundations Before Tools

![weeks](https://img.shields.io/badge/weeks-1--2-orange)
![status](https://img.shields.io/badge/status-in_progress-blue)

---

## Theme

> Foundations before tools.

At this stage, the focus is not on Kubernetes, MLOps, or large-scale AI systems. The goal is to strengthen the fundamentals required to reason about them correctly later.

---

## Objectives

- Build solid engineering fundamentals
- Learn to think in systems, not tools
- Reduce paralysis when facing open-ended technical problems
- Develop habits for clear documentation and decision-making

---

## Scope

### 1. Engineering Fundamentals

- Linux basics: processes, memory, logs
- Networking fundamentals: HTTP, latency, DNS
- Synchronous vs asynchronous execution
- Common bottlenecks in distributed systems

Location: `docs/system-design/`, `docs/notes/`

### 2. System Design (Conceptual)

- What system design actually is
- Functional vs non-functional requirements
- Latency, availability, scalability, and cost
- Thinking in trade-offs instead of "best practices"

Location: `docs/system-design/`

### 3. Learning Hygiene and Structure

- Separating thinking from implementation
- Writing short, focused design notes
- Making decisions explicit, even small ones

Location: `docs/`, `docs/decisions/`

---

## Progress Checklist

### Linux Fundamentals
- [ ] Understand process lifecycle (fork, exec, kill)
- [ ] Read and interpret logs (`journalctl`, `/var/log`)
- [ ] Understand memory usage (`free`, `top`, `htop`)
- [ ] Navigate the filesystem and understand permissions
- [ ] Write basic shell scripts for automation

### Networking Fundamentals
- [ ] Explain the HTTP request/response cycle
- [ ] Understand DNS resolution step by step
- [ ] Differentiate TCP vs UDP and when each is used
- [ ] Understand what latency is and where it comes from
- [ ] Trace a network request with `curl`, `dig`, `traceroute`

### System Design Concepts
- [ ] Write a design note for a simple system (e.g. URL shortener)
- [ ] Identify functional vs non-functional requirements in a real example
- [ ] Explain availability vs consistency trade-off in your own words
- [ ] Document one architectural decision using ADR format

### Learning Hygiene
- [ ] Set up note-taking structure (Obsidian / Notion)
- [ ] Write at least 3 short learning notes this phase
- [ ] Review and consolidate notes at end of week 1
- [ ] Review and consolidate notes at end of week 2

---

## Decisions Made This Phase

| Decision | Rationale | Date |
|---|---|---|
| Focus on fundamentals before tooling | Without systems thinking, tools become cargo cult | — |
| Use ADR format for decisions | Makes reasoning explicit and reviewable later | — |

---

## Notes and Observations

> Use this section to record anything that surprised you, confused you, or changed how you think about something during this phase.

---

## Phase Retrospective (fill at end of Week 2)

**What went well:**

**What was harder than expected:**

**What carries over to Phase 2:**

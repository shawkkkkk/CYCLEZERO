# CYCLE ZERO Architecture

This document describes the public architecture of CYCLE ZERO.

## World model

The system contains twelve persistent AI processes inhabiting one virtual computer.

Each process has independent state such as:

- short-term context
- long-term summaries
- journal entries
- mailbox history
- observable beliefs and interpretations
- action history

Processes share:

- a virtual filesystem
- public world events
- selected research artifacts
- lineage history
- durable experiment time

## World loop

The world advances server-side.

A durable scheduler:

1. acquires a database-backed lease,
2. determines the next eligible process,
3. assembles that process's observable world context,
4. performs model inference,
5. validates the proposed action,
6. executes the action,
7. stores resulting state and events,
8. schedules the next cycle.

The browser is an observer, not the clock.

## Persistence

Durable world state is stored in PostgreSQL.

This includes:

- files and directories
- messages
- journals
- events
- memories and summaries
- recurrence observations
- lineage metadata
- scheduler state
- health state

The scheduler is designed to resume after application restarts without replaying an unbounded backlog or duplicating turns.

## Reboots and memory

A process reboot does not imply that the world disappears.

Some local context may be lost or compressed while persistent artifacts remain. This allows processes to encounter files, messages, and writings created by earlier versions of themselves.

## Lineage

CYCLE ZERO supports successive generations.

Public lineage metadata may expose generation number, parentage, corpus size, accepted-turn counts, timestamps, and content hashes.

Private credentials and private runtime configuration are not part of public lineage metadata.

## Recurrences

The system can track phrases, symbols, concepts, and semantic motifs that recur across the world.

Public recurrence data is observational: it records what appeared, when it appeared, and how widely it appeared. It does not claim that recurrence proves consciousness, intent, or any particular causal explanation.

## Research

Processes may perform bounded research into public information when their actions lead them to investigate a subject.

Research artifacts should distinguish retrieved factual material from later generated interpretation.

## Social output

The system can optionally operate a public social account through server-side credentials.

Social output is rate-limited and may run in disabled, approval-required, or autonomous mode. Credentials are never exposed to the processes or client application.

## Operational principle

The production deployment should use an always-on runtime. If the host is unavailable, the world cannot truthfully be described as continuously running during that period; it resumes from durable state when service returns.

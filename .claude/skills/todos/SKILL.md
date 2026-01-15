---
name: todos
description: Manages project todos via REST API. Use when the user asks to create, view, update, or delete todos, list tasks by project, check task status, or filter by due date. Requires the Noetect app to be running.
version: 1
---

# Todos Management

## Overview

Manages todos via the Noetect REST API. The API handles all validation, ID generation, timestamps, and ordering automatically.

## Port Discovery

The server writes its port to a discoverable location. Extract it with:

```bash
PORT=$(cat ~/Library/Application\ Support/com.firstloop.noetect/serverport.json | grep -o '"port":[0-9]*' | cut -d: -f2)
```

## API Endpoints

All endpoints use POST with JSON body at `http://localhost:$PORT`:

| Endpoint | Description |
|----------|-------------|
| `/api/todos/create` | Create a new todo |
| `/api/todos/list` | List todos (with optional project filter) |
| `/api/todos/get` | Get a single todo by ID |
| `/api/todos/update` | Update a todo |
| `/api/todos/delete` | Delete a todo |
| `/api/todos/projects` | List all projects |
| `/api/todos/tags` | List all tags |
| `/api/todos/archive` | Archive a todo |
| `/api/todos/unarchive` | Unarchive a todo |
| `/api/todos/archived` | List archived todos |

## Create Todo

```bash
curl -s -X POST "http://localhost:$PORT/api/todos/create" \
  -H "Content-Type: application/json" \
  -d '{"title": "My todo", "project": "work"}'
```

## List Todos

```bash
# All active todos
curl -s -X POST "http://localhost:$PORT/api/todos/list" \
  -H "Content-Type: application/json" \
  -d '{}'

# Todos for a specific project
curl -s -X POST "http://localhost:$PORT/api/todos/list" \
  -H "Content-Type: application/json" \
  -d '{"project": "work"}'
```

## Update Todo

```bash
curl -s -X POST "http://localhost:$PORT/api/todos/update" \
  -H "Content-Type: application/json" \
  -d '{"todoId": "todo-123", "updates": {"status": "done"}}'
```

## How Claude Should Use This Skill

Always start by getting the server port, then use the appropriate endpoint.

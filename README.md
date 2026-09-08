# Task API

This is a simple **CRUD API** built using **Python and FastAPI** as part of my **FlyRank Backend Internship Week 2 Assignment**.

The API allows users to create, view, update, and delete tasks.

## What I Used

* Python
* FastAPI
* Uvicorn
* Pydantic

## How to Run the Project

First, create a virtual environment:

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

Install the required packages:

```bash
pip install -r requirements.txt
```

Start the server:

```bash
uvicorn main:app --reload
```

The API will run at:

```text
http://127.0.0.1:8000
```

## Swagger UI

FastAPI provides a Swagger page where all the API endpoints can be tested.

Open this in your browser:

```text
http://127.0.0.1:8000/docs
```

From there, I can test the GET, POST, PUT, and DELETE operations.

## API Endpoints

| Method | Endpoint      | What it does                 |
| ------ | ------------- | ---------------------------- |
| GET    | `/`           | Shows basic API information  |
| GET    | `/health`     | Checks if the API is running |
| GET    | `/tasks`      | Gets all tasks               |
| GET    | `/tasks/{id}` | Gets one task by ID          |
| POST   | `/tasks`      | Creates a new task           |
| PUT    | `/tasks/{id}` | Updates a task               |
| DELETE | `/tasks/{id}` | Deletes a task               |

## Example Task

A task looks like this:

```json
{
  "id": 1,
  "title": "Learn FastAPI",
  "done": false
}
```

## Example Requests

### Get all tasks

```bash
curl http://127.0.0.1:8000/tasks
```

### Get one task

```bash
curl http://127.0.0.1:8000/tasks/1
```

### Create a new task

```bash
curl -X POST http://127.0.0.1:8000/tasks ^
  -H "Content-Type: application/json" ^
  -d "{\"title\":\"Buy milk\"}"
```

The new task is created with `done: false`.

### Update a task

```bash
curl -X PUT http://127.0.0.1:8000/tasks/1 ^
  -H "Content-Type: application/json" ^
  -d "{\"title\":\"Learn FastAPI Updated\",\"done\":true}"
```

### Delete a task

```bash
curl -X DELETE http://127.0.0.1:8000/tasks/2
```

A successful delete returns:

```text
204 No Content
```

## Error Example

If I try to get a task that does not exist:

```bash
curl http://127.0.0.1:8000/tasks/99
```

The API returns:

```json
{
  "error": "Task 99 not found"
}
```

## How the Data is Stored

For this assignment, I used a simple **in-memory list** instead of a database.

This means the tasks are only stored while the server is running. If the server is restarted, the tasks go back to the original example tasks.

## Project Files

```text
flyrank-task-api/
├── main.py
├── requirements.txt
├── README.md
└── .gitignore
```

## Assignment

This project was created for the **FlyRank Backend Internship — Week 2 Assignment A1: Build Your First CRUD API**.

## Author

Keshav

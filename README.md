# 🧠 Async Job Processing Backend

An asynchronous, Dockerized backend service built with FastAPI, PostgreSQL, Redis, and Celery that allows users to submit and track jobs (e.g., data processing tasks like `square_sum`, `cube_sum`) in real time.

---

## 🚀 Features Implemented

- ✅ Job Submission — Submit data processing jobs (`square_sum`, `cube_sum`)
- ✅ Job Status Polling — Check status: `PENDING`, `IN_PROGRESS`, `SUCCESS`, `FAILED`
- ✅ Job Result Retrieval — Fetch computed result after job completion
- ✅ Async Background Processing — Uses Celery with Redis to process jobs asynchronously
- ✅ JWT Authentication — Secure endpoints via `/register` and `/login`
- ✅ Rate Limiting — User-level request throttling using middleware
- ✅ Job Listing — View all jobs submitted by the authenticated user
- ✅ Swagger/OpenAPI Docs — Interactive API docs at `http://localhost:8000/docs`
- ✅ Dockerized Environment — One-command launch with Docker Compose
- ✅ Unit Tests — Coverage for job creation, status checks, and error handling

> ⚠️ Not Implemented Yet:
> - Job expiration and cleanup
> - Pagination and filtering of past jobs

---

## 📦 Tech Stack

- Language: Python 3.10+
- Web Framework: FastAPI (async)
- Database: PostgreSQL
- ORM: SQLAlchemy (async)
- Task Queue: Celery
- Broker: Redis
- Auth: JWT tokens (via `python-jose`, `passlib`)
- Containerization: Docker, Docker Compose
- Testing: Pytest + HTTPX + ASGITransport

---

## 📪 API Endpoints

> All job-related endpoints require a JWT token in the Authorization header:  
> `Authorization: Bearer <access_token> . Here do not Write Bearer while putting JWT token in the Authorization header`

# 🔐 Auth API

## Endpoints

### POST /register — Register a new user  
### `POST /login` — Login to get JWT token  

# 🧮 Jobs

# POST /jobs — Create Job  
# GET /jobs/{job_id}/status — Get Job Status  
# GET /jobs/{job_id}/result — Get Job Result  
# GET /jobsList/ — List All Jobs  

# All Request/Response Samples

```json
// Register Request
{
  "username": "yourname",
  "password": "yourpassword"
}

// Login Request
{
  "username": "yourname",
  "password": "yourpassword"
}

// Login Response
{
  "access_token": "<JWT_TOKEN>",
  "token_type": "bearer"
}

// Create Job Request
{
  "data": [1, 2, 3],
  "operation": "square_sum"
}

// Create Job Response
{
  "job_id": "uuid",
  "status": "PENDING"
}

// Job Status Response
{
  "status": "IN_PROGRESS"
}

// Job Result Response
{
  "status": "SUCCESS",
  "result": 14
}

// Jobs List Response
{
  "jobs": [
    {
      "job_id": "uuid",
      "data": [1, 2, 3],
      "operation": "square_sum",
      "status": "SUCCESS",
      "result": 14
    }
  ]
}

🐳 Running the Project
Prerequisites
Docker & Docker Compose installed

Python 3.10+ (optional for local development)

Start All Services
bash
Copy
Edit
docker-compose up --build
Access:

App: http://localhost:8000

Docs: http://localhost:8000/docs

🧪 Running Tests
bash
Copy
Edit
docker-compose exec api pytest --disable-warnings --cov=app
Tests include:

Auth flow

Job creation

Status tracking

Result verification

Invalid operation handling

📁 Project Structure
css
Copy
Edit
.
├── app/
│   ├── main.py
│   ├── models.py
│   ├── tasks.py
│   ├── db.py
│   └── api/
│       ├── routes.py
│       ├── auth.py
│       ├── rate_limit.py
│       ├── deps.py
│       └── schemas.py
├── tests/
│   └── test_jobs.py
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
└── README.md
📝 Future Enhancements
 Job expiration & automatic cleanup

 Pagination & filtering in /jobsList

 Retry/timeout mechanisms

 Admin dashboard

📬 Contact
Built with ❤️ by [Your Name]
Feel free to connect on GitHub or LinkedIn

yaml
Copy
Edit

---

✅ After copying the content, create a `README.md` file in your project root folder and paste it there.

Let me know if you’d like a `.txt` version or want it zipped for upload.

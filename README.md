⭐ AttentionAI – Complete Technical Architecture & Stack Breakdown.
1. Backend Technologies
Programming Language

Python 3.11 – Core backend language

Web Framework

FastAPI 0.110.1 – Modern async API framework

Uvicorn 0.25.0 – ASGI server for running FastAPI

Computer Vision & AI (MediaPipe + OpenCV)

MediaPipe 0.10.18

mp_face_mesh – 468 facial landmark detection

mp_hands – 21 hand landmarks

mp_pose – 33 pose landmarks

OpenCV 4.11.0.86 (headless & contrib)

Image pre-processing & frame operations

Machine Learning Libraries

NumPy 1.26.4 – Vectorized math

JAX 0.7.1 + JAXlib 0.7.1 – Under-the-hood ML acceleration (MediaPipe dep.)

TensorFlow Lite – Embedded inference engine

SciPy 1.16.3 – Scientific computation

Database

MongoDB – NoSQL DB for storing sessions + analytics

Motor 3.3.1 – Async MongoDB driver

PyMongo 4.5.0 – Base MongoDB driver

Data Handling

Pydantic 2.6.4+ – Validation & schema enforcement

Protobuf 4.25.8 – Serialization used by MediaPipe

Utilities

python-dotenv – ENV loader

CORS middleware – For cross-origin access

2. Frontend Technologies
Programming

JavaScript (ES6+)

JSX (React)

Framework

React 19.0.0

React DOM 19.0.0

React Router DOM 7.5.1

UI Library

Shadcn/UI

Radix UI (40+ components including Dialog, Tabs, Progress, Alert Dialog, Badge, etc.)

Styling

Tailwind CSS 3.4.17

PostCSS, Autoprefixer

tailwindcss-animate

clsx, cva, tailwind-merge

Icons

Lucide React 0.507.0 (Eye, Hand, Smile, User, Activity, AlertCircle, Camera etc.)

HTTP Client

Axios 1.8.4

Notifications

Sonner 2.0.3

Forms

React Hook Form 7.56.2

Zod 3.24.4

@hookform/resolvers 5.0.1

Build

React Scripts 5.0.1

CRACO 7.1.0

Webpack + Babel

3. APIs & Endpoints
Session Management

POST /api/sessions – Create session

GET /api/sessions – Get all sessions

GET /api/sessions/{id} – Fetch specific

POST /api/sessions/{id}/end – End session

Real-Time Frame Analysis

POST /api/analyze

Accepts: multipart/form-data (image blob)

Query: session_id

Returns: tracking results + attention score

Analytics

GET /api/sessions/{id}/analytics

Health Check

GET /api/

4. Core Features & Algorithms
1. Multi-Modal Tracking System
🟦 Eye Tracking

Iris landmarks: 468, 473

30-frame buffer

Movement threshold: 0.015

Score: max(0, 100 - avg_movement × 5000)

🟩 Hand Tracking

Wrist landmark: 0

20-frame buffer

Threshold: 0.02

Score: max(0, 100 - avg_movement × 3000)

🟨 Expression Analysis

Mouth landmarks: 61, 291, 13, 14

Smile ratio = width / height

25-frame buffer

Threshold: 0.3

🟥 Posture Tracking

Nose: 0

Shoulders: 11, 12

10-frame buffer

Threshold: 0.025

Score: max(0, 100 - avg_movement × 2500)

2. Attention Score Formula
Attention Score =
  (eye_stability × 0.35) +
  (hand_stability × 0.25) +
  (expression_stability × 0.25) +
  (posture_stability × 0.15)

3. Smoothing Algorithm

5-frame rolling average for:

Attention

Eye

Hand

Expression

Posture

4. Alert System

Eye < 60 → High eye movement

Hand < 70 → Excessive hand movement

Expression < 70 → Frequent expression change

Posture < 65 → Posture instability

Face not detected → Critical alert

5. WebRTC & Media APIs

getUserMedia() – Webcam video stream

<video> – Live preview

<canvas> – Capture frames

canvas.toBlob() – Convert image

requestAnimationFrame() – Smooth rendering

FormData() – Upload frame

6. MongoDB Data Schemas
tracking_sessions
{
  "id": "UUID",
  "student_name": "String",
  "start_time": "DateTime",
  "end_time": "DateTime",
  "attention_score": "Float",
  "eye_movements": "Integer",
  "hand_movements": "Integer",
  "expression_changes": "Integer",
  "posture_changes": "Integer",
  "duration_seconds": "Integer"
}

frame_analyses
{
  "session_id": "UUID",
  "timestamp": "DateTime",
  "attention_score": "Float",
  "eye_stability": "Float",
  "hand_stability": "Float",
  "expression_stability": "Float",
  "posture_stability": "Float",
  "alerts": ["String"]
}

7. Buffers & Data Structures

deque() (fixed size)

Eye: 30 frames

Hands: 20 frames

Expressions: 25

Head pose: 15

Posture: 10

Smoothing: 5

8. Performance Optimizations

Backend analysis: 0.5 FPS (every 2 sec)

Frontend render: 60 FPS

JPEG compression: 85%

Async DB operations

Removed landmark drawing → Faster frame processing

9. External Dependencies

Google MediaPipe ML models

TensorFlow Lite (XNNPACK optimized)

MongoDB cloud/self-host

ENV variables:

MONGO_URL

DB_NAME

CORS_ORIGINS

REACT_APP_BACKEND_URL

10. Development Tools
Backend

pytest

black

isort

flake8

mypy

Frontend

ESLint

Babel

Prettier

✅ This is now a fully structured, presentation-ready, investor-ready, documentation-ready technical architecture.

# Micro-Entrepreneur Growth Platform

A full-stack CRM platform designed to help micro-entrepreneurs manage customers, referrals, marketing, and their digital presence from a single platform.

## Features

* Full-stack CRM built with **React, FastAPI, and SQLAlchemy**
* **JWT-based authentication** for secure user access
* Customer management and referral tracking
* Analytics dashboard for monitoring business activity
* **Google Gemini API** integration for generating marketing content
* Multi-platform content generation for **WhatsApp, Instagram, Facebook, LinkedIn, and Twitter**
* **Redis-backed rate limiting** for API protection
* **Celery + Redis** for asynchronous notification scheduling
* Digital Presence Builder with responsive website templates
* Live website template preview
* Mobile-responsive React interface

## Tech Stack

**Frontend**

* React
* TypeScript
* HTML/CSS

**Backend**

* FastAPI
* Python
* SQLAlchemy
* JWT Authentication

**Database**

* PostgreSQL

**AI & Background Processing**

* Google Gemini API
* Redis
* Celery

## Architecture

```text
React Frontend
      |
      v
 FastAPI Backend
      |
  +---+----------------+
  |                    |
  v                    v
PostgreSQL           Redis
  |                    |
  |                 Celery
  |                    |
  |                    v
  +------------> Background Tasks
```

## Core Modules

### CRM

Manage customers, track referrals, and maintain customer-related information through a centralized dashboard.

### AI Marketing Content

Gemini API generates platform-specific marketing content based on the business, target audience, and selected tone.

### Notification System

Celery workers process notification and scheduling tasks asynchronously through Redis, preventing long-running operations from blocking API endpoints.

### Digital Presence Builder

Users can select website templates, customize their digital presence, and preview the website in real time with a mobile-responsive interface.

## Installation

```bash
git clone <repository-url>
cd micro-entrepreneur-platform
```

### Backend

```bash
cd backend
pip install -r requirements.txt
```

Create a `.env` file:

```env
DATABASE_URL=your_database_url
JWT_SECRET=your_secret_key
GEMINI_API_KEY=your_gemini_api_key
REDIS_URL=redis://localhost:6379/0
```

Start the FastAPI server:

```bash
uvicorn main:app --reload
```

### Celery Worker

```bash
celery -A tasks worker --loglevel=info
```

### Frontend

```bash
cd frontend
npm install
npm run dev
```

## API Example

Create a customer:

```http
POST /customers
```

```json
{
  "name": "Rahul",
  "email": "rahul@example.com"
}
```

Generate marketing content:

```http
POST /content/generate
```

```json
{
  "platform": "Instagram",
  "prompt": "Promote our new product"
}
```

Schedule a notification:

```http
POST /notifications
```

The notification is pushed to the Redis queue and processed asynchronously by a Celery worker.

## Project Structure

```text
micro-entrepreneur-platform/
│
├── frontend/
│   ├── src/
│   ├── components/
│   └── pages/
│
├── backend/
│   ├── main.py
│   ├── models/
│   ├── schemas/
│   ├── routes/
│   ├── services/
│   └── tasks/
│
├── .env
├── requirements.txt
└── README.md
```

## Key Highlights

* Built a scalable **full-stack CRM architecture**
* Integrated **AI-powered marketing automation**
* Implemented **asynchronous task processing** using Celery and Redis
* Added **API rate limiting** for controlled resource usage
* Developed a responsive **Digital Presence Builder** with live previews

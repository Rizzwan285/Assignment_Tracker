# 📚 Assignment Tracking System

A full-stack web application for managing academic assignments with a modern, colorful UI. Built with FastAPI backend and React frontend.

![Assignment Tracker](https://img.shields.io/badge/Status-Complete-success)
![Python](https://img.shields.io/badge/Python-3.9+-blue)
![React](https://img.shields.io/badge/React-18+-61DAFB)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688)

## ✨ Features

- ✅ **Complete CRUD Operations** - Create, Read, Update, and Delete assignments
- 📊 **Live Statistics Dashboard** - Real-time count of Pending, In Progress, and Completed assignments
- 🎨 **Vibrant UI Design** - Modern card-based layout with colorful status indicators
- 📅 **Smart Date Formatting** - Human-readable dates (e.g., "Jan 21, 2026 at 4:07 PM")
- 🔄 **Status Cycling** - Click status badges to cycle through Pending → In Progress → Completed
- 🎯 **Expandable Forms** - Minimalist collapsed form that expands on demand
- ⚡ **Real-time Updates** - Instant UI refresh after any operation
- 🗄️ **Persistent Storage** - PostgreSQL database with automatic timestamps

## 🛠️ Technology Stack

### Backend
- **FastAPI** - Modern Python web framework
- **SQLAlchemy** - SQL toolkit and ORM
- **PostgreSQL** - Relational database
- **Pydantic** - Data validation
- **Uvicorn** - ASGI server

### Frontend
- **React** - UI library
- **Lucide React** - Icon system
- **date-fns** - Date formatting
- **Vanilla CSS** - Custom styling with design tokens

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Python 3.9+** - [Download](https://www.python.org/downloads/)
- **Node.js 16+** - [Download](https://nodejs.org/)
- **PostgreSQL** - [Download](https://www.postgresql.org/download/)
- **Git** - [Download](https://git-scm.com/downloads)

## 🚀 Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/Rizzwan285/Assign_Track_test.git
cd Assign_Track_test
```

### 2. Backend Setup

#### a. Create Virtual Environment
```bash
cd backend
python -m venv venv
```

#### b. Activate Virtual Environment
**Windows:**
```bash
venv\Scripts\activate
```

**macOS/Linux:**
```bash
source venv/bin/activate
```

#### c. Install Dependencies
```bash
pip install fastapi uvicorn sqlalchemy psycopg2-binary pydantic
```

#### d. Configure Database
1. Make sure PostgreSQL is running
2. Create database (default credentials: `postgres`/`postgres`):
```bash
python create_db.py
```

**Or manually using PostgreSQL:**
```sql
CREATE DATABASE assignment_db;
```

#### e. Environment Variables (Optional)
If your PostgreSQL has different credentials, set the `DATABASE_URL`:

**Windows:**
```bash
set DATABASE_URL=postgresql://username:password@localhost:5432/assignment_db
```

**macOS/Linux:**
```bash
export DATABASE_URL=postgresql://username:password@localhost:5432/assignment_db
```

### 3. Frontend Setup

```bash
cd ../frontend
npm install
```

## ▶️ Running the Application

### Start Backend Server

```bash
cd backend
# Ensure virtual environment is activated
uvicorn main:app --reload
```

Backend will run at: **http://localhost:8000**
- API Docs (Swagger): **http://localhost:8000/docs**

### Start Frontend Server

Open a **new terminal** and run:

```bash
cd frontend
npm start
```

Frontend will run at: **http://localhost:3000**

## 📡 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/assignments` | Create a new assignment |
| `GET` | `/api/assignments` | Get all assignments |
| `GET` | `/api/assignments/{id}` | Get assignment by ID |
| `PATCH` | `/api/assignments/{id}` | Update assignment |
| `DELETE` | `/api/assignments/{id}` | Delete assignment |

### Example API Request

**Create Assignment:**
```bash
curl -X POST "http://localhost:8000/api/assignments" \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Data Structures Lab",
    "description": "Complete binary tree implementation"
  }'
```

## 📁 Project Structure

```
Assign_Track_test/
├── backend/
│   ├── main.py              # FastAPI application and routes
│   ├── models.py            # SQLAlchemy database models
│   ├── schemas.py           # Pydantic validation schemas
│   ├── database.py          # Database connection setup
│   ├── create_db.py         # Database creation script
│   └── reset_db.py          # Database reset utility
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── AssignmentForm.js    # Create assignment form
│   │   │   ├── AssignmentList.js    # Assignment cards display
│   │   │   └── StatsBar.js          # Statistics dashboard
│   │   ├── api.js           # API service layer
│   │   ├── App.js           # Main application component
│   │   ├── App.css          # Component styles
│   │   └── index.css        # Global styles & design tokens
│   └── package.json
└── README.md
```

## 🎨 Data Model

### Assignment
```typescript
{
  id: number                 // Auto-generated
  title: string              // Required
  description: string?       // Optional
  status: string            // "Pending" | "In Progress" | "Completed"
  created_time: datetime    // Auto-generated
  updated_time: datetime    // Auto-updated
}
```

## 🔧 Troubleshooting

### Database Connection Failed
- Ensure PostgreSQL service is running
- Verify database credentials in `database.py`
- Check if `assignment_db` database exists

### Port Already in Use
If port 8000 or 3000 is busy:

**Backend (change to port 8001):**
```bash
uvicorn main:app --reload --port 8001
```

**Frontend:** React will automatically prompt for another port

### Module Not Found Errors
Ensure all dependencies are installed:
```bash
# Backend
pip install -r requirements.txt  # if available
# or install manually as shown in Setup

# Frontend
npm install
```

## 🧪 Testing the Application

1. **Create Assignment**: Fill the form and click "Create Assignment"
2. **View Stats**: Check the stats bar updates with counts
3. **Cycle Status**: Click on status badges to change status
4. **Delete**: Hover over a card and click the trash icon

## 📝 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `DATABASE_URL` | `postgresql://postgres:postgres@localhost:5432/assignment_db` | PostgreSQL connection string |

## 👥 Contributors

- Muhammad Rizwan ([@Rizzwan285](https://github.com/Rizzwan285))

## 📄 License

This project is created for educational purposes.

## 🙏 Acknowledgments

- Built as part of OELP Assignment
- UI inspired by modern design patterns
- Icons by [Lucide](https://lucide.dev/)

---

**Made with ❤️ using FastAPI and React**

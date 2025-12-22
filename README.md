# KIT MATRIX

A modern academic portal for Kalpataru Institute of Technology (KIT) students to access notes, assignments, question papers, model papers, circulars, and syllabus materials. Built with the MERN stack (MongoDB, Express.js, React, Node.js).

## 📋 Table of Contents

- [Goal to Achieve](#goal-to-achieve)
- [Requirements](#requirements)
- [Database Setup](#database-setup)
- [Installation & Setup](#installation--setup)
- [Running the Application](#running-the-application)
- [Features](#features)
- [ToDo](#todo)
- [Tech Stack](#tech-stack)

## 🎯 Goal to Achieve

**KIT MATRIX** is designed to be a centralized platform where:

1. **Lecturers can:**
   - Register and login with secure authentication
   - Upload notes organized by branch, year, subject, and module
   - Upload assignments for students
   - Post announcements (text and video)
   - Share circulars (college announcements)
   - Manage all academic resources with full CRUD operations

2. **Students can:**
   - Access all notes, assignments, and resources without authentication
   - Browse materials by branch (CSE, ISE, ECE, AIML, Civil, Mechanical)
   - Filter resources by year, subject, and module
   - Search for specific materials
   - Download/view notes, question papers, model papers, circulars, and syllabus

The platform ensures that only authenticated lecturers can add, edit, or delete content, while students have read-only access to all materials.

## 📦 Requirements

### Prerequisites

- **Node.js** (v16 or higher) - [Download](https://nodejs.org/)
- **MongoDB** (v5 or higher) - [Download](https://www.mongodb.com/try/download/community)
- **npm** (comes with Node.js) or **yarn**
- **Git** (for cloning the repository)

### Software Versions Used

- Node.js: v16+
- MongoDB: v5+
- React: v19.1.1
- Express: v5.1.0
- MongoDB Driver (Mongoose): v8.19.4

## 🗄️ Database Setup

### MongoDB Installation

1. **Download MongoDB Community Server:**
   - Visit [MongoDB Download Center](https://www.mongodb.com/try/download/community)
   - Download the appropriate version for your OS (Windows/Mac/Linux)
   - Run the installer and follow the setup wizard

2. **Start MongoDB Service:**
   
   **Windows:**
   - MongoDB usually starts automatically as a service
   - Or manually start: `net start MongoDB`
   - Or run: `mongod` in terminal

   **Mac/Linux:**
   ```bash
   brew services start mongodb-community  # Mac (if installed via Homebrew)
   # OR
   sudo systemctl start mongod  # Linux
   ```

3. **Verify MongoDB is Running:**
   - MongoDB runs on `mongodb://127.0.0.1:27017` by default
   - You can verify by running: `mongosh` or `mongo` (older versions)
   - Or check if port 27017 is listening

4. **Database Configuration:**
   - The application will automatically create a database named `kit_circle` when you first run the backend
   - No manual database creation needed
   - Collections (Lecturer, Note) will be created automatically

### MongoDB Connection String

The backend uses this connection string (configurable via environment variable):
```
mongodb://127.0.0.1:27017/kit_circle
```

To use a different MongoDB instance, set the `MONGO_URI` environment variable:
```bash
# Windows PowerShell
$env:MONGO_URI="mongodb://your-host:27017/kit_circle"

# Mac/Linux
export MONGO_URI="mongodb://your-host:27017/kit_circle"
```

## 🚀 Installation & Setup

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd KIT-Circle
```

### 2. Backend Setup

```bash
# Navigate to backend directory
cd Backend

# Install dependencies
npm install

# The backend will use these packages:
# - express: Web framework
# - mongoose: MongoDB ODM
# - bcryptjs: Password hashing
# - jsonwebtoken: JWT authentication
# - cors: Cross-origin resource sharing
```

### 3. Frontend Setup

```bash
# Navigate to frontend directory (from project root)
cd frontend

# Install dependencies
npm install

# Frontend uses:
# - React: UI library
# - React Router: Navigation
# - Tailwind CSS: Styling
# - Vite: Build tool
```

## ▶️ Running the Application

### Step 1: Start MongoDB

Make sure MongoDB is running on your system (see [Database Setup](#database-setup) above).

**Check if MongoDB is running:**
```bash
# Windows
netstat -ano | findstr :27017

# Mac/Linux
lsof -i :27017
```

### Step 2: Start Backend Server

Open a terminal/command prompt:

```bash
# Navigate to backend directory
cd Backend

# Start the backend server
npm run dev

# Or if nodemon is not installed:
node Script.js
```

**Expected Output:**
```
MongoDB connected
Backend running on port 4000
```

The backend API will be available at: `http://localhost:4000`

**Available API Endpoints:**
- `GET /` - Health check
- `POST /api/auth/register` - Register new lecturer
- `POST /api/auth/login` - Login lecturer
- `POST /api/auth/reset-password` - Request OTP for password reset
- `POST /api/auth/verify-otp` - Verify OTP
- `POST /api/auth/set-password` - Reset password after OTP verification
- `GET /api/notes` - Get all notes (public)
- `POST /api/notes` - Create note (requires authentication)
- `DELETE /api/notes/:id` - Delete note (requires authentication)

### Step 3: Start Frontend Development Server

Open a **new terminal/command prompt** (keep backend running):

```bash
# Navigate to frontend directory
cd frontend

# Start the development server
npm run dev
```

**Expected Output:**
```
  VITE v7.x.x  ready in xxx ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
```

The frontend will be available at: `http://localhost:5173`

### Step 4: Access the Application

1. Open your browser and navigate to: `http://localhost:5173`
2. You'll see the landing page
3. Register a new lecturer account or login if you already have one
4. Start adding notes and resources!

### Important Notes:

- **Backend must be running** before the frontend can make API calls
- **MongoDB must be running** before the backend can start
- For password reset OTP, check the **backend terminal console** (OTP is logged there for development)

## ✨ Features

### ✅ Implemented Features

- 🔐 **Authentication System**
  - Lecturer registration and login
  - JWT-based authentication
  - Password reset via OTP
  - Secure password hashing (bcrypt)

- 📚 **Notes Management**
  - Add notes (lecturers only)
  - View notes (public access)
  - Delete notes (lecturers only)
  - Filter by branch, year, subject, and module
  - Search functionality

- 🎨 **User Interface**
  - Dark/Light theme toggle
  - Responsive design (mobile-friendly)
  - Breadcrumb navigation
  - Modern UI with Tailwind CSS

- 🔒 **Security**
  - Protected routes (only authenticated lecturers can add/delete)
  - JWT token validation
  - Password encryption

### 🚧 In Progress / Planned Features

See [ToDo](#todo) section below.

## 📝 ToDo

### High Priority

- [ ] **Assignments Management**
  - [ ] Add assignment upload form (lecturers)
  - [ ] Backend API for assignments (CRUD)
  - [ ] Frontend page to view assignments
  - [ ] Filter assignments by branch, year, subject

- [ ] **Question Papers & Model Papers**
  - [ ] Add upload forms for QP and Model Papers
  - [ ] Backend APIs for both
  - [ ] Frontend pages to view and download

- [ ] **Circulars Management**
  - [ ] Add circular upload form
  - [ ] Backend API for circulars
  - [ ] Display circulars page
  - [ ] Support for text and video announcements

- [ ] **Syllabus Management**
  - [ ] Add syllabus upload form
  - [ ] Backend API for syllabus
  - [ ] Frontend page to view syllabus by branch/year

### Medium Priority

- [ ] **Email Integration**
  - [ ] Integrate nodemailer or SendGrid for OTP emails
  - [ ] Send registration confirmation emails
  - [ ] Email notifications for new resources

- [ ] **File Upload**
  - [ ] Implement file upload to cloud storage (AWS S3, Cloudinary, etc.)
  - [ ] Support for PDF, DOCX, images, videos
  - [ ] File size and type validation

- [ ] **Enhanced Search**
  - [ ] Full-text search across all resources
  - [ ] Advanced filters (date range, author, etc.)
  - [ ] Search suggestions and autocomplete

- [ ] **User Profile**
  - [ ] Lecturer profile page
  - [ ] Edit profile functionality
  - [ ] View uploaded resources history

### Low Priority / Future Enhancements

- [ ] **Admin Dashboard**
  - [ ] Admin role with additional permissions
  - [ ] Analytics and statistics
  - [ ] User management

- [ ] **Notifications**
  - [ ] In-app notifications
  - [ ] Email notifications for students
  - [ ] Push notifications (PWA)

- [ ] **Student Features**
  - [ ] Student registration (optional)
  - [ ] Favorite/bookmark resources
  - [ ] Download history

- [ ] **Additional Features**
  - [ ] Comments/feedback on resources
  - [ ] Rating system for notes
  - [ ] Share resources via social media
  - [ ] Export resources to PDF

## 🛠️ Tech Stack

### Frontend
- **React** v19.1.1 - UI library
- **React Router** v7.9.6 - Client-side routing
- **Tailwind CSS** v4.1.17 - Utility-first CSS framework
- **Vite** v7.1.7 - Build tool and dev server

### Backend
- **Node.js** - Runtime environment
- **Express.js** v5.1.0 - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** v8.19.4 - MongoDB object modeling
- **JWT** (jsonwebtoken) v9.0.2 - Authentication tokens
- **bcryptjs** v2.4.3 - Password hashing
- **CORS** v2.8.5 - Cross-origin resource sharing

### Development Tools
- **ESLint** - Code linting
- **Nodemon** - Auto-restart server during development

## 📄 License

ISC

## 👥 Contributors

Built for Kalpataru Institute of Technology (KIT), Tiptur.

---

**Note:** Make sure MongoDB is running before starting the backend server. For password reset OTP, check the backend console output (development mode only).

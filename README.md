# Safety Questionnaire Admin System

A comprehensive full-stack safety questionnaire application with user/admin authentication, role-based access control, and questionnaire submission functionality.

## Features

- **User Authentication**: Sign up/sign in with JWT-based authentication
- **Role-based Access Control**: Separate user and admin interfaces
- **Safety Questionnaire**: 16-question safety assessment with Yes/No answers
- **Admin Dashboard**: View all users and questionnaire submissions
- **User Dashboard**: Personalized dashboard with questionnaire access
- **Responsive Design**: Modern, clean interface using Tailwind CSS
- **Real-time Validation**: Client-side form validation with password strength requirements

## Tech Stack

### Frontend
- React.js with TypeScript
- Tailwind CSS for styling
- Context API for state management
- TanStack Query for data fetching
- Shadcn/ui components

### Backend
- Node.js with Express.js
- In-memory storage (MemStorage)
- JWT authentication
- bcryptjs for password hashing
- Comprehensive API endpoints

## Prerequisites

- Node.js (v16 or higher)
- npm

## Installation & Setup

1. **Clone the repository** (if applicable)
   ```bash
   git clone <repository-url>
   cd safety-questionnaire-app
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Variables**
   Create a `.env` file in the root directory:
   ```env
   JWT_SECRET=your-secret-key-change-in-production
   PORT=5000
   ```

4. **Start the application**
   ```bash
   npm run dev
   ```

   The application will be available at `http://localhost:5000`

## Default Admin User

The system automatically creates a default admin user:
- **Email**: admin@example.com
- **Password**: admin123
- **Role**: admin

You can use these credentials to access the admin panel immediately after starting the application.

## API Endpoints

### Authentication
- `POST /api/auth/signup` - Register new user
- `POST /api/auth/signin` - User login
- `GET /api/auth/check-status` - Verify token status

### User Routes
- `GET /api/user/dashboard` - Get user dashboard data

### Questionnaire Routes
- `POST /api/questionnaire/submit` - Submit questionnaire answers
- `GET /api/questionnaire/user` - Get user's questionnaire history

### Admin Routes (Admin Only)
- `GET /api/admin/users` - Get all registered users
- `GET /api/admin/feedback` - Get all questionnaire submissions

## Usage Guide

### For Regular Users

1. **Sign Up/Sign In**
   - Navigate to the application
   - Create an account or sign in with existing credentials
   - Password must meet strength requirements:
     - At least 8 characters
     - 1 uppercase letter
     - 1 lowercase letter
     - 1 number
     - 1 special character

2. **Dashboard Access**
   - After login, you'll see your personalized dashboard
   - View your user information and role

3. **Complete Questionnaire**
   - Click "Start Questionnaire" from the dashboard
   - Answer all 16 safety questions with Yes/No responses
   - Track your progress with the progress bar
   - Submit your responses

### For Admin Users

1. **Admin Login**
   - Sign in with admin credentials
   - Access the Admin Panel button in the navigation

2. **View Users**
   - See all registered users in a table format
   - View user details including ID, username, email, and role

3. **Monitor Questionnaire Submissions**
   - View all submitted questionnaires
   - See compliance scores and status for each submission
   - Track submission dates and user details

## Security Features

- **JWT Authentication**: Secure token-based authentication
- **Password Hashing**: bcryptjs for secure password storage
- **Role-based Access**: Separate user and admin routes
- **Input Validation**: Comprehensive client and server-side validation
- **Protected Routes**: Authentication required for all protected endpoints

## Development

### Project Structure

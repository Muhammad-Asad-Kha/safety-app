# replit.md

## Overview

This is a comprehensive full-stack Safety Questionnaire Admin System built with React.js and Node.js. The application provides user authentication, role-based access control, and a 16-question safety assessment system. It features separate interfaces for regular users and administrators, with JWT-based authentication and in-memory storage (currently using MemStorage, but configured for PostgreSQL with Drizzle ORM).

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Overall Architecture
- **Frontend**: React.js with TypeScript, built with Vite
- **Backend**: Node.js with Express.js
- **Database**: Currently using in-memory storage (MemStorage), but configured for PostgreSQL with Drizzle ORM
- **Authentication**: JWT-based token authentication
- **UI Framework**: Tailwind CSS with Shadcn/ui components
- **State Management**: React Context API for global state
- **Data Fetching**: TanStack Query for server state management

### Key Design Decisions
1. **Monorepo Structure**: Client and server code coexist in the same repository with shared schema definitions
2. **Type Safety**: Full TypeScript implementation across frontend and backend
3. **Component-Based UI**: Modular component architecture using Shadcn/ui
4. **Role-Based Access**: Clear separation between user and admin functionalities
5. **Custom Routing**: Simple page switching using React state instead of external routing libraries

## Key Components

### Frontend Structure
- **App.tsx**: Main application component handling routing and authentication state
- **AuthContext**: Global authentication state management
- **Pages**: Dashboard, AdminDashboard, Questionnaire, AuthForm, NotFound
- **Components**: Reusable UI components including Navbar, form elements
- **Hooks**: Custom hooks for toast notifications and mobile detection

### Backend Structure
- **routes.ts**: API endpoint definitions for auth, user management, and questionnaire submissions
- **storage.ts**: Data access layer with MemStorage implementation
- **schema.ts**: Shared database schema definitions using Drizzle ORM
- **vite.ts**: Development server configuration

### Authentication System
- **JWT Tokens**: Stored in localStorage for session management
- **Role-Based Access**: 'user' and 'admin' roles with different permissions
- **Password Security**: bcrypt hashing with strength validation
- **Default Admin**: Automatically created admin user (admin@example.com / admin123)

### Questionnaire System
- **16 Safety Questions**: Predefined safety assessment questions
- **Yes/No Responses**: Simple boolean answers stored as JSON
- **Progress Tracking**: Visual progress indicator during completion
- **Submission History**: Users can view their past submissions

## Data Flow

### Authentication Flow
1. User submits login credentials
2. Server validates credentials and generates JWT token
3. Token stored in localStorage and included in API requests
4. Protected routes verify token and user permissions

### Questionnaire Flow
1. Authenticated user navigates to questionnaire
2. Questions loaded from predefined array
3. User answers are stored in local state
4. On submission, answers sent to server with user identification
5. Server stores questionnaire response linked to user

### Admin Dashboard Flow
1. Admin user accesses protected admin routes
2. Server fetches all users and questionnaire submissions
3. Enhanced dashboard displays:
   - Total users, users who submitted, total submissions, and pending approvals
   - Detailed user table with user information
   - Comprehensive submitted forms table with user IDs and submission times
   - Modal dialog for viewing complete form responses with detailed compliance analysis
   - Export functionality for individual submissions
   - Dedicated approval management section with approve/reject functionality
4. Real-time statistics calculated from submission data

### Form Approval System
1. All submitted forms start with 'pending' approval status
2. Admin can access dedicated "Form Approvals" tab
3. Approval dashboard shows statistics (pending, approved, rejected)
4. Admin can review each form in detail with compliance scoring
5. Admin can approve or reject forms directly from review modal
6. Approval actions are tracked with admin ID and timestamp
7. Status badges clearly indicate approval state across all interfaces

### Form Upload and Management System
1. Admin can access "Form Management" tab to create new questionnaires
2. Form creation interface allows:
   - Custom form title and description
   - Dynamic question addition/removal
   - Question type selection (Yes/No, Text, Number)
   - Required field configuration
3. All created forms are stored with metadata (creator, creation date)
4. Form listing shows all questionnaires with status and details
5. Form preview functionality shows complete form structure
6. Default safety questionnaire automatically created on system initialization
7. Future questionnaire submissions will reference specific form IDs

## External Dependencies

### Frontend Dependencies
- **React Ecosystem**: React 18, TypeScript, Vite
- **UI Components**: Radix UI primitives, Tailwind CSS
- **State Management**: TanStack Query, React Context
- **Form Handling**: React Hook Form with Zod validation
- **Icons**: Lucide React icons

### Backend Dependencies
- **Server Framework**: Express.js
- **Database**: Drizzle ORM, PostgreSQL driver (@neondatabase/serverless)
- **Authentication**: JWT, bcryptjs
- **Validation**: Zod schema validation
- **Development**: tsx for TypeScript execution

### Development Tools
- **Build Tool**: Vite with React plugin
- **TypeScript**: Full type checking across the stack
- **Database Migration**: Drizzle Kit for schema management
- **Code Quality**: ESLint, Prettier (implied by structure)

## Deployment Strategy

### Development Setup
- **Single Command**: `npm run dev` starts both frontend and backend
- **Hot Reload**: Vite provides fast development feedback
- **TypeScript Checking**: `npm run check` for type validation
- **Database Push**: `npm run db:push` for schema updates

### Production Build
- **Frontend Build**: Vite compiles React app to static files
- **Backend Build**: esbuild bundles Node.js server code
- **Environment Variables**: Database URL and JWT secret required
- **Static Serving**: Express serves built frontend files

### Database Configuration
- **Current State**: In-memory storage for development
- **Production Ready**: PostgreSQL with Drizzle ORM configured
- **Migration System**: Drizzle Kit handles schema changes
- **Connection**: Neon Database serverless PostgreSQL driver

### Security Considerations
- **JWT Secret**: Must be set in production environment
- **Password Hashing**: bcrypt with salt rounds
- **Input Validation**: Zod schemas for all user inputs
- **CORS**: Configured for production domains
- **Session Management**: Token expiration and refresh strategies

The application is designed to be easily deployable on platforms like Replit, Vercel, or traditional hosting with minimal configuration changes required.
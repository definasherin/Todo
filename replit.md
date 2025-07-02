# TaskFlow - Modern Task Management Application

## Overview

TaskFlow is a full-stack task management application built with React, Express.js, and PostgreSQL. The application provides a modern, intuitive interface for creating, managing, and organizing tasks with features like priority levels, due dates, and filtering capabilities. It uses Replit's authentication system for secure user management.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **UI Library**: Radix UI components with shadcn/ui styling system
- **Styling**: Tailwind CSS with custom CSS variables for theming
- **State Management**: TanStack Query (React Query) for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Form Handling**: React Hook Form with Zod validation
- **Build Tool**: Vite with React plugin

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Database**: PostgreSQL with Drizzle ORM
- **Authentication**: Replit Auth with OpenID Connect integration
- **Session Management**: Express sessions stored in PostgreSQL
- **API Design**: RESTful API with JSON responses

## Key Components

### Database Schema
The application uses three main tables:
- **sessions**: Required for Replit Auth session storage
- **users**: User profiles with Replit integration (required for auth)
- **tasks**: Task entities with title, description, priority, completion status, and due dates

### Authentication System
- **Provider**: Replit Auth using OpenID Connect
- **Session Storage**: PostgreSQL-backed sessions with connect-pg-simple
- **Middleware**: Custom authentication middleware for API route protection
- **User Management**: Automatic user creation/updates via upsert operations

### Task Management Features
- **CRUD Operations**: Full create, read, update, delete functionality
- **Priority Levels**: Low, medium, high priority classification
- **Status Tracking**: Completed/incomplete task states
- **Due Dates**: Optional deadline management
- **Filtering**: Search by title, filter by status and priority
- **Real-time Updates**: Optimistic updates with query invalidation

### UI Components
- **Design System**: shadcn/ui components built on Radix UI primitives
- **Responsive Design**: Mobile-first approach with Tailwind CSS
- **Modals**: Task creation/editing and deletion confirmation dialogs
- **Toast Notifications**: User feedback for actions and errors
- **Loading States**: Skeleton components and loading indicators

## Data Flow

1. **Authentication Flow**:
   - User accesses application → Replit Auth check → Login redirect if needed
   - Successful auth → User session creation → Access to protected routes

2. **Task Operations**:
   - Client requests → Authentication middleware → Route handlers
   - Database operations via Drizzle ORM → Response with updated data
   - Client cache updates via TanStack Query

3. **Real-time Updates**:
   - Optimistic updates for immediate UI feedback
   - Server validation and database persistence
   - Cache invalidation and refetch on conflicts

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: PostgreSQL database connection
- **drizzle-orm & drizzle-kit**: Database ORM and migration tools
- **@tanstack/react-query**: Server state management
- **@radix-ui/react-***: UI component primitives
- **react-hook-form**: Form state management
- **zod**: Schema validation
- **tailwindcss**: Utility-first CSS framework

### Authentication Dependencies
- **openid-client**: OpenID Connect client implementation
- **passport**: Authentication middleware
- **express-session**: Session management
- **connect-pg-simple**: PostgreSQL session store

### Development Dependencies
- **vite**: Build tool and development server
- **typescript**: Type safety
- **@replit/vite-plugin-***: Replit-specific development tools

## Deployment Strategy

### Development Environment
- **Server**: Vite development server with HMR
- **API**: Express server with file watching via tsx
- **Database**: PostgreSQL connection via environment variables
- **Build Process**: Separate client and server build steps

### Production Build
- **Client**: Vite production build to `dist/public`
- **Server**: ESBuild bundle to `dist/index.js`
- **Assets**: Static file serving via Express
- **Database**: Drizzle schema push for deployment

### Environment Configuration
- **DATABASE_URL**: PostgreSQL connection string (required)
- **SESSION_SECRET**: Session encryption key
- **REPL_ID & ISSUER_URL**: Replit Auth configuration
- **NODE_ENV**: Environment detection

## Changelog
- July 01, 2025. Initial setup

## User Preferences

Preferred communication style: Simple, everyday language.
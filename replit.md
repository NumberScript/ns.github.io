# Overview

This is a NumberScript IDE - a mathematical computing environment with an integrated development environment (IDE) interface. The application allows users to write, edit, and execute NumberScript code for mathematical computations, with features like real-time mathematical work display, cloud storage integration, and collaborative editing capabilities. The IDE provides a VS Code-like interface specifically designed for mathematical programming and education.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
The frontend is built using React with TypeScript and follows a component-based architecture. The main IDE interface consists of modular components including an Activity Bar, Sidebar, Code Editor, Math Work Panel, and Bottom Panel. The UI uses shadcn/ui components with Radix UI primitives for consistent design and accessibility. The application uses Wouter for client-side routing and TanStack Query for state management and API communication.

## Backend Architecture
The backend follows a minimal Express.js server architecture with TypeScript. The server uses a plugin-based approach with Vite integration for development and serves the React frontend in production. The API routes are organized under `/api` prefix and use a storage interface pattern for data persistence, with both memory storage and database storage implementations available.

## Data Storage Solutions
The application uses a dual storage approach:
- **Primary Database**: PostgreSQL with Drizzle ORM for structured data persistence, including user accounts, projects, and collaborative sessions
- **Memory Storage**: In-memory storage implementation for development and testing
- **Cloud Storage**: Integration with Google Drive and GitHub for external file storage and version control

The database schema includes tables for users (with OAuth authentication), projects (with collaboration support), and sessions (for real-time collaboration tracking).

## Authentication and Authorization
The system implements OAuth-based authentication supporting multiple providers:
- **Google OAuth**: For Google Drive integration and user authentication
- **GitHub OAuth**: For GitHub repository integration and version control
- **Session Management**: PostgreSQL-backed session storage with connect-pg-simple

User accounts support multiple authentication methods (local, Google, GitHub) with avatar and profile management.

## External Dependencies

### Database and ORM
- **PostgreSQL**: Primary database using Neon Database serverless PostgreSQL
- **Drizzle ORM**: Type-safe database operations with automatic migrations
- **connect-pg-simple**: PostgreSQL session store for Express sessions

### Authentication Services
- **Google OAuth API**: User authentication and Google Drive API access
- **GitHub OAuth API**: User authentication and repository access
- **Google Drive API**: Cloud file storage and collaboration
- **GitHub API**: Repository management and version control

### UI and Frontend Libraries
- **shadcn/ui**: UI component library built on Radix UI primitives
- **Radix UI**: Accessible component primitives for complex UI elements
- **TailwindCSS**: Utility-first CSS framework with custom design tokens
- **React Hook Form**: Form state management with validation
- **TanStack Query**: Server state management and caching

### Mathematical Computing
- **Custom NumberScript Engine**: Domain-specific language parser and evaluator for mathematical expressions
- **Real-time Evaluation**: Live mathematical computation with step-by-step work display
- **Mathematical Functions**: Built-in support for calculus, algebra, and statistical operations

### Development and Build Tools
- **Vite**: Frontend build tool and development server
- **TypeScript**: Static type checking across the entire application
- **ESBuild**: Fast JavaScript bundler for production builds
- **PostCSS**: CSS processing with TailwindCSS integration

### Optional LMS Integrations
- **Canvas LMS API**: Learning management system integration for educational environments
- **Google Classroom API**: Assignment and course management integration

The architecture supports real-time collaboration through WebSocket connections, automatic file synchronization with cloud providers, and extensible plugin system for additional mathematical functions and integrations.
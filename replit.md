# Overview

This is a food delivery mobile application called "السريع ون" (Quick One) built for the Yemeni market. The application connects customers with restaurants and handles the complete food delivery workflow including browsing restaurants, ordering food, payment processing, and order tracking. It features a modern Arabic-first interface optimized for mobile devices and includes admin and driver portals for managing operations.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture

The frontend is built as a Single Page Application (SPA) using React with TypeScript. Key architectural decisions include:

- **Component Library**: Uses shadcn/ui components built on Radix UI primitives for consistent, accessible UI components
- **Styling**: Tailwind CSS with custom CSS variables for theming, supporting both light and dark modes
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: Zustand for global cart state with persistence to localStorage
- **Data Fetching**: TanStack Query (React Query) for server state management and caching
- **Forms**: React Hook Form with Zod validation schemas
- **Internationalization**: Arabic-first design with RTL (Right-to-Left) support using Noto Sans Arabic font

The application follows a mobile-first responsive design pattern with a maximum width container to simulate a mobile app experience on desktop browsers.

## Backend Architecture

The backend follows a REST API design using Express.js with TypeScript:

- **Framework**: Express.js with TypeScript for type safety
- **Database Layer**: Drizzle ORM with PostgreSQL (Neon serverless) for database operations
- **Authentication**: Custom Replit-based OIDC authentication with session management
- **Session Storage**: PostgreSQL-backed sessions using connect-pg-simple
- **API Structure**: RESTful endpoints organized by resource (restaurants, orders, categories)
- **Error Handling**: Centralized error handling middleware
- **Logging**: Custom request/response logging for API endpoints

## Data Storage Solutions

- **Primary Database**: PostgreSQL via Neon serverless platform
- **ORM**: Drizzle ORM for type-safe database queries and migrations
- **Schema Design**: Includes tables for users, restaurants, categories, menu items, orders, offers, and sessions
- **Relationships**: Proper foreign key relationships between entities (restaurants -> categories, orders -> restaurants, etc.)
- **Data Persistence**: Client-side cart state persisted to localStorage using Zustand persist middleware

## Authentication and Authorization

- **Authentication Provider**: Replit OIDC integration for user authentication
- **Session Management**: Server-side sessions stored in PostgreSQL with configurable TTL
- **Role-Based Access**: Support for customer, admin, and driver roles with route-level authorization
- **Security**: HTTP-only secure cookies, CSRF protection, and proper session handling

## External Dependencies

- **Database**: Neon PostgreSQL serverless database
- **Authentication**: Replit OIDC service for user authentication
- **Development**: Vite for development server and build tooling
- **Fonts**: Google Fonts for Arabic typography (Noto Sans Arabic)
- **Icons**: Font Awesome for consistent iconography
- **Deployment**: Designed for Replit hosting environment with custom error overlay and development tools

The architecture supports a complete food delivery workflow with real-time order tracking, multi-role access (customers, drivers, admins), and Arabic language support throughout the user experience.
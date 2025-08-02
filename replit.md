# Hotel AI Receptionist - System Architecture

## Overview

This is a full-stack hotel management application with an AI-powered multilingual chat interface. The system combines a React frontend with an Express.js backend, featuring real-time chat capabilities, voice interaction, booking management, automated email notifications, and self-monitoring capabilities. The application is designed as a modern hotel receptionist system that can handle guest inquiries in multiple languages, process bookings, and manage hotel operations through both AI chat and traditional management interfaces.

## User Preferences

Preferred communication style: Simple, everyday language.

## Recent Changes (January 31, 2025)

✓ Built complete multilingual AI hotel receptionist system
✓ Added voice interaction (speech-to-text and text-to-speech)
✓ Implemented self-monitoring system with error tracking
✓ Created automated owner notification system
✓ Added comprehensive dashboard with analytics
✓ Integrated OpenAI GPT-4o for multilingual responses with fallback system
✓ Built email notification service for bookings
✓ Added system health monitoring and auto-shutdown
✓ Created detailed README with deployment instructions
✓ Tested all features - multilingual chat, voice, monitoring fully operational
✓ Prepared complete GitHub-ready codebase with documentation

## System Architecture

The application follows a monorepo structure with clear separation between client and server code:

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack Query for server state management
- **UI Framework**: Radix UI components with shadcn/ui styling system
- **Styling**: Tailwind CSS with CSS variables for theming
- **Build Tool**: Vite for development and production builds

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **Database ORM**: Drizzle ORM with PostgreSQL dialect
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **AI Integration**: OpenAI GPT-4o for chat responses and language detection
- **Email Service**: Nodemailer for automated notifications

## Key Components

### Database Schema
The system uses four main entities:
- **Users**: Authentication and user management
- **Bookings**: Hotel reservations with status tracking, pricing, and guest information
- **Conversations**: Chat session management with language and status tracking
- **Messages**: Individual chat messages with sender identification and timestamps

### AI Chat System
- **Language Detection**: Automatic detection of guest language (English, French, Spanish)
- **Intent Recognition**: Identifies booking-related intents and actions
- **Response Generation**: Context-aware responses using OpenAI GPT-4o
- **Multi-language Support**: Handles conversations in multiple languages

### Booking Management
- **Room Types**: Multiple room categories with dynamic pricing
- **Status Tracking**: Pending, confirmed, and cancelled booking states
- **Price Calculation**: Automatic total price computation based on dates and room type
- **Email Notifications**: Automated confirmations and owner notifications

### UI Components
- **Dashboard Interface**: Multi-section dashboard with live chat, bookings, analytics, and logs
- **Real-time Updates**: Automatic refresh of conversations and booking data
- **Responsive Design**: Mobile-first approach with adaptive layouts
- **Component Library**: Comprehensive UI component system using Radix primitives

## Data Flow

### Chat Flow
1. Guest initiates conversation through chat interface
2. Message is sent to backend API endpoint
3. Language detection occurs using OpenAI
4. AI generates contextual response based on hotel information
5. Response is stored in database and returned to frontend
6. Frontend updates chat interface in real-time

### Booking Flow
1. AI chat identifies booking intent or manual booking creation
2. Booking data is validated using Zod schemas
3. Price calculation occurs based on room type and duration
4. Booking is stored in database with pending status
5. Email notifications are sent to guest and hotel owner
6. Dashboard updates reflect new booking status

### Authentication Flow
- In-memory storage implementation for development
- User sessions managed through backend storage interface
- Extensible design allows for database persistence integration

## External Dependencies

### Core Dependencies
- **Database**: Neon Database (PostgreSQL) for production data storage
- **AI Service**: OpenAI API for chat functionality and language processing
- **Email Service**: SMTP provider (Gmail/custom) for automated notifications
- **Build Tools**: Vite, ESBuild for frontend and backend compilation

### Development Dependencies
- **TypeScript**: Type safety across entire stack
- **Drizzle Kit**: Database migrations and schema management
- **React Hook Form**: Form handling with validation
- **Date-fns**: Date manipulation and formatting

## Deployment Strategy

### Development Environment
- **Frontend**: Vite dev server with HMR and error overlay
- **Backend**: Direct TypeScript execution with tsx
- **Database**: Drizzle push for schema synchronization
- **Hot Reload**: Automatic server restart on file changes

### Production Build
- **Frontend**: Vite production build with asset optimization
- **Backend**: ESBuild compilation to single JavaScript bundle
- **Database**: Migration-based deployment using Drizzle Kit
- **Environment**: Node.js production server with optimized configurations

### Configuration Management
- Environment variables for database URLs, API keys, and SMTP settings
- Separate configurations for development and production environments
- Type-safe configuration validation and error handling

The architecture emphasizes modularity, type safety, and real-time functionality while maintaining a clear separation of concerns between the AI chat system, booking management, and user interface components.
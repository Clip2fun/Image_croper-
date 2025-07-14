# Rounder - Image Shape Cropping Application

## Overview

Rounder is a React-based web application that allows users to upload images and crop them into various shapes. The application provides a visual interface for selecting different geometric shapes (diamond, circle, heart, star, etc.) and applying them as masks to uploaded images. Users can also adjust dimensions and export the cropped results.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **Styling**: Tailwind CSS with shadcn/ui component library
- **State Management**: React hooks (useState, useEffect) for local state
- **Routing**: Wouter for lightweight client-side routing
- **UI Components**: Radix UI primitives with custom Tailwind styling

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Runtime**: Node.js with ES modules
- **Development**: tsx for TypeScript execution in development
- **Production**: esbuild for server bundling

### Database Layer
- **ORM**: Drizzle ORM for type-safe database operations
- **Database**: PostgreSQL (configured for Neon Database)
- **Schema**: Centralized in `/shared/schema.ts` for frontend/backend sharing
- **Migrations**: Drizzle Kit for database schema management

## Key Components

### Frontend Components
1. **App.tsx** - Main application wrapper with routing and providers
2. **Home.tsx** - Main page with image cropping interface
3. **ImageCropper.tsx** - Canvas-based image cropping component
4. **ShapeSelector.tsx** - UI for selecting crop shapes
5. **DimensionControls.tsx** - Controls for image dimensions and file upload

### Backend Components
1. **server/index.ts** - Express server setup with middleware
2. **server/routes.ts** - API route registration (currently minimal)
3. **server/storage.ts** - Data access layer with in-memory implementation
4. **server/vite.ts** - Vite development server integration

### Shared Components
1. **shared/schema.ts** - Database schema definitions and TypeScript types

## Data Flow

### Image Processing Flow
1. User uploads image file through file input
2. Image is loaded into HTML Image element
3. Canvas API renders image with shape mask applied
4. User can adjust dimensions and re-crop
5. Final image can be downloaded/exported

### Shape Rendering
- Shapes are defined as Path2D objects in `/lib/shapes.ts`
- Canvas uses composite operations to apply shape masks
- Supports 12 different shapes: diamond, oval, circle, hexagon, triangle, pentagon, octagon, heart, star, square, rounded square, and arrow

## External Dependencies

### Frontend Dependencies
- **UI Framework**: React 18+ with TypeScript
- **Styling**: Tailwind CSS with PostCSS
- **Component Library**: Radix UI primitives
- **State Management**: @tanstack/react-query for server state
- **Routing**: wouter for client-side routing
- **Form Handling**: react-hook-form with zod validation

### Backend Dependencies
- **Server**: Express.js with TypeScript
- **Database**: Drizzle ORM with PostgreSQL driver (@neondatabase/serverless)
- **Development**: tsx for TypeScript execution
- **Build**: esbuild for production bundling

### Development Dependencies
- **Build Tool**: Vite with React plugin
- **TypeScript**: Full TypeScript support with strict mode
- **Development Tools**: Replit-specific plugins for development environment

## Deployment Strategy

### Build Process
1. **Frontend**: Vite builds React app to `/dist/public`
2. **Backend**: esbuild bundles server code to `/dist/index.js`
3. **Database**: Drizzle migrations applied via `npm run db:push`

### Environment Configuration
- `DATABASE_URL` required for PostgreSQL connection
- `NODE_ENV` determines development vs production mode
- Supports deployment to Replit with specific configurations

### Production Setup
- Express serves built React app as static files
- API routes prefixed with `/api`
- Database migrations managed through Drizzle Kit
- Single-server deployment model

## Recent Changes

### January 2025 - Content Enhancement & SEO Improvements
- Added comprehensive "How to Use" section with step-by-step instructions
- Implemented "Free-to-Use Benefits" section highlighting key features
- Created detailed FAQ section addressing common user questions
- Added SEO-optimized meta tags, Open Graph, and Twitter cards
- Enhanced page structure for better search engine visibility
- Improved user experience with clear visual guidance

### Canvas Overlay Implementation
- Fixed semi-transparent overlay to show outside shape boundaries only
- Image within shape area displays clearly without obstruction
- Implemented proper "window" effect using canvas composite operations
- Resolved JavaScript errors with canvas API compatibility

## Development Notes

### Database Schema
Currently minimal with just a users table for future authentication features. The in-memory storage implementation suggests the main functionality doesn't require persistent storage yet.

### Canvas Implementation
The application heavily relies on HTML5 Canvas API for image manipulation, with custom utility functions for drawing and shape path generation. Recent improvements include proper overlay rendering for better visual feedback.

### Responsive Design
Uses Tailwind's responsive utilities and includes mobile-specific hooks and components for optimal mobile experience.

### SEO Implementation
- Comprehensive meta tags for search engines
- Open Graph and Twitter card support
- Structured content with FAQ section
- User-friendly instructions and benefits highlighting

### Future Considerations
- Authentication system (schema already prepared)
- Image persistence/storage
- Advanced editing features
- Export format options
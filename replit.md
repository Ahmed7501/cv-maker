# AI-Powered CV Maker

## Overview

An AI-powered CV/resume builder application that allows users to create professional resumes with AI-enhanced content. The application provides multiple professional templates, real-time preview, and AI-powered text enhancement using Claude (Anthropic). Users can input their personal information, work experience, education, skills, and projects, then choose from various professionally-designed templates to generate a polished CV.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework**: React with TypeScript, using Vite as the build tool and development server.

**UI Component Library**: Shadcn/ui with Radix UI primitives - A comprehensive design system built on top of Radix UI primitives providing accessible, customizable components. The application uses the "new-york" style variant with neutral base colors and CSS variables for theming.

**Styling**: Tailwind CSS with custom design tokens and responsive breakpoints. The design follows Fluent Design principles emphasizing clarity, efficiency, and professional polish. Typography uses Inter as the primary font with specialized fonts for CV templates (Georgia, Poppins, Playfair Display).

**State Management**: React Query (TanStack Query) for server state management and data fetching. Local component state using React hooks for UI state.

**Routing**: Wouter for lightweight client-side routing.

**Responsive Design**:
- Desktop (≥1024px): Split-screen layout with 40% form editor and 60% preview
- Tablet (768px-1023px): Stacked layout with tabbed navigation
- Mobile (<768px): Full-width stacked with floating preview button

### Backend Architecture

**Server Framework**: Express.js with TypeScript running on Node.js.

**API Design**: RESTful API with a single AI enhancement endpoint (`POST /api/ai/enhance`) that processes text through Claude AI.

**Middleware**: Standard Express middleware stack including JSON body parsing with raw body preservation for verification purposes.

**Development Tools**: Custom Vite integration for HMR (Hot Module Replacement) in development mode, with Replit-specific plugins for enhanced development experience.

### Data Storage

**Current Implementation**: In-memory storage using a custom `MemStorage` class implementing the `IStorage` interface. This provides basic CRUD operations for user management.

**Schema Management**: Drizzle ORM configured with PostgreSQL dialect, though currently using in-memory storage. The schema is defined in `shared/schema.ts` with Zod validation schemas for runtime type safety.

**Data Models**:
- Personal information (name, contact details, social links)
- Professional summary
- Work experience (job title, company, dates, descriptions)
- Education (degree, institution, graduation dates)
- Skills (categorized skill sets)
- Projects (with descriptions)

**Rationale**: The in-memory storage provides a simple starting point for development and demonstration. The infrastructure is prepared for PostgreSQL migration via Drizzle ORM when persistence is needed.

### Form Validation & Type Safety

**Schema Validation**: Zod schemas define the structure and validation rules for all CV data and API requests. This provides both runtime validation and TypeScript type inference.

**Form Handling**: React Hook Form with Zod resolvers for declarative form validation and state management.

### Template System

**Design**: Five professional CV templates with distinct visual styles:
- **Modern**: Two-column layout with dark sidebar
- **Classic**: Traditional single-column serif design
- **Creative**: Asymmetric layout with colored sidebar
- **Executive**: Timeline-based professional layout
- **Minimalist**: Clean, sparse design with minimal decoration

Each template is a separate React component that accepts CV data and renders it according to its design system.

### Print/Export Functionality

Uses the browser's native print functionality (`window.print()`) which allows users to save CVs as PDFs through the print dialog. Templates are optimized with print-specific CSS classes.

## External Dependencies

### AI Service Integration

**Provider**: Anthropic Claude API
- **Model**: claude-sonnet-4-20250514 (latest Sonnet model)
- **Purpose**: Text enhancement for CV content (summaries, experience descriptions, project descriptions)
- **Authentication**: API key via environment variable (`ANTHROPIC_API_KEY`)

**Enhancement Types**:
- Professional summary refinement
- Work experience achievement-focused rewriting
- Project description technical enhancement

### Database

**Planned**: PostgreSQL via Neon Database (`@neondatabase/serverless`)
- Connection string via `DATABASE_URL` environment variable
- Drizzle ORM for schema management and queries
- Currently configured but not actively used (in-memory storage in use)

### UI Components

**Radix UI Primitives**: Comprehensive set of unstyled, accessible components including accordions, dialogs, dropdowns, popovers, tabs, tooltips, and form controls.

**Additional Libraries**:
- `react-day-picker`: Date selection for education/experience dates
- `cmdk`: Command palette component
- `lucide-react`: Icon library
- `date-fns`: Date formatting and manipulation
- `class-variance-authority`: Utility for managing component variants
- `tailwind-merge`: Intelligent Tailwind class merging

### Development Tools

**Replit Integration**: Custom Vite plugins for Replit development environment including error modals, cartographer for code navigation, and development banners.

**Build Tools**:
- Vite for frontend bundling and dev server
- esbuild for backend compilation
- TypeScript compiler for type checking
- PostCSS with Tailwind and Autoprefixer

### Session Management

**Library**: `connect-pg-simple` - PostgreSQL session store for Express (prepared for when database is active)
# Pre Purchase Inspection LLC - Replit Configuration

## Overview

This is a full-stack web application for Pre Purchase Inspection LLC, a vehicle inspection service. The application manages vehicle inspections, user authentication, payment processing, and PDF report generation. It features separate interfaces for inspectors, administrators, dealers, and includes public verification functionality.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **Styling**: Tailwind CSS with shadcn/ui component library
- **State Management**: TanStack Query (React Query) for server state
- **Routing**: Wouter for client-side routing
- **PDF Generation**: React-PDF for inspection reports
- **Forms**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with TypeScript
- **Framework**: Express.js
- **Authentication**: Passport.js with local strategy and sessions
- **File Upload**: Multer with image optimization using Sharp
- **PDF Processing**: React-PDF server-side rendering
- **Push Notifications**: Web Push API with VAPID keys

### Data Storage Solutions
- **Database**: PostgreSQL with Neon serverless
- **ORM**: Drizzle ORM for type-safe database operations
- **Session Store**: PostgreSQL-based session storage
- **File Storage**: Local file system with cleanup scheduler

## Key Components

### User Management
- Multi-role authentication (Inspector, Admin, Dealer)
- User registration with approval workflow
- Password hashing with scrypt
- Session-based authentication with secure cookies

### Inspection System
- Complete vehicle inspection forms with multiple categories
- VIN validation and vehicle data fetching from NHTSA API
- Photo upload with automatic optimization
- Status tracking (Draft, Completed, Review)
- Pass/Fail determination based on inspection criteria

### Payment Integration
- Square payment processing
- Payment status tracking
- Dealership billing system
- Cost management ($99 per inspection)

### Notification System
- Real-time push notifications using Web Push API
- Admin notifications for new registrations
- Browser notification support with sound alerts
- Email notifications via SendGrid

### Report Generation
- PDF report generation with vehicle details and photos
- QR code integration for verification
- Public report verification by VIN
- Dealership billing reports

## Data Flow

1. **Inspection Creation**: Inspector creates inspection → Photos uploaded → Results recorded → PDF generated
2. **Payment Processing**: Square payment → Status updated → Email confirmation sent
3. **Admin Workflow**: New registration → Admin notification → Approval → User activated
4. **Public Verification**: VIN entered → Database lookup → Report displayed if available

## External Dependencies

### APIs and Services
- **NHTSA VPIC API**: Vehicle identification and specifications
- **Google Cloud Vision**: Image processing capabilities (configured but not actively used)
- **AWS Rekognition**: Alternative image processing service
- **SendGrid**: Email delivery service
- **Square**: Payment processing

### NPM Packages
- **Database**: `@neondatabase/serverless`, `drizzle-orm`
- **Authentication**: `passport`, `express-session`
- **File Processing**: `multer`, `sharp`
- **PDF**: `@react-pdf/renderer`
- **UI Components**: Various `@radix-ui` packages
- **Validation**: `zod`, `@hookform/resolvers`

## Deployment Strategy

### Build Process
- **Development**: `npm run dev` - TSX for server, Vite for client
- **Production Build**: `npm run build` - Vite build + ESBuild for server
- **Database**: `npm run db:push` for schema deployment

### Environment Configuration
- **Platform**: Replit with Cloud Run deployment
- **Database**: PostgreSQL 16 with automatic provisioning
- **Sessions**: Database-backed session storage
- **Static Files**: Express static serving for uploads and public assets

### Production Settings
- Secure cookies in production
- Proxy trust for Cloud Run
- CORS configuration for cross-origin requests
- Rate limiting and security headers

## Recent Changes
- June 25, 2025: Added Admin "Saved Drafts" tab allowing admins to view and continue editing all saved inspections from any inspector
- June 25, 2025: Enhanced Milad page with comprehensive monthly breakdown showing detailed inspection statistics (Individual vs Dealership counts with specific dealership breakdowns)
- June 25, 2025: Removed payment instruction from dealership PDF bill footer for cleaner professional appearance
- June 25, 2025: Fixed critical database connection pool exhaustion issue preventing user login
- June 24, 2025: Updated "Emissions Pass" PDF display to show text results only (YES/NO/N/A) without color status boxes
- June 24, 2025: Replaced service selection page with improved three-page navigation flow and professional styling
- June 23, 2025: Implemented asterisk mapping fix for PDF reports ensuring critical safety items display properly
- June 23, 2025: Initial setup

## User Preferences

Preferred communication style: Simple, everyday language.
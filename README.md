# Tuwaiq-Smart-Shield
Project Overview
Tuwaiq Smart Shield (TSH) is a modern Saudi Arabian intelligent mountain road protection system that leverages advanced AI, sensor technology, and government integration to monitor and protect mountainous regions from natural hazards.
Key Features
1. Intelligent Monitoring System
Real-time monitoring of 20+ mountains across Saudi Arabia
AI-powered hazard detection and risk assessment
Sensor integration for environmental data collection
Automatic alert generation based on risk levels
2. Government Integration
Absher Integration: Official government authentication and citizen verification
Tawakkalna Integration: Health status and travel compliance verification
Seamless data sharing with relevant authorities
3. Citizen Reporting System
Mobile-friendly interface for reporting hazards
Photo and document upload capability (S3 storage)
Location-based reporting with GPS coordinates
Real-time status tracking of submitted reports
4. Alert Management
5 risk levels (Low, Medium, High, Critical, Extreme)
Color-coded alert system for quick identification
Active alert dashboard showing current threats
Historical alert tracking and analysis
5. AI-Powered Features
Intelligent hazard prediction models
Natural language processing for report analysis
Automated risk assessment
Pattern recognition for early warning
Technical Stack
Frontend
Framework: React 19 with TypeScript
Styling: Tailwind CSS 4
Routing: Wouter
UI Components: shadcn/ui
State Management: React Query + tRPC
Mobile-First Design: Responsive for all devices
Backend
Runtime: Node.js with Express 4
API: tRPC 11 (Type-safe RPC)
Database: MySQL with Drizzle ORM
Authentication: Manus OAuth
File Storage: AWS S3
Testing: Vitest
Database Schema
Users Table
User ID, OpenID, Name, Email
Login Method, Role (user/admin)
Timestamps (created, updated, lastSignedIn)
Mountains Table
Mountain ID, Name (Arabic/English)
Elevation, GPS Coordinates
Region, Timestamps
Alerts Table
Alert ID, Mountain ID, Title, Description
Risk Level (1-5), Type (rockfall/weather/sensor/report)
Location, Active Status, Timestamps
Reports Table
Report ID, User ID, Mountain ID
Title, Description, Location, GPS Coordinates
Status (new/reviewing/resolved)
Image URL/Key, Timestamps
Uploaded Files Table
File ID, User ID, Report ID
File Name, S3 Key, S3 URL
MIME Type, File Size, Timestamps
API Endpoints
Mountains
GET /api/trpc/mountains.getAll - Get all mountains
GET /api/trpc/mountains.getById - Get specific mountain
Alerts
GET /api/trpc/alerts.getActive - Get active alerts
GET /api/trpc/alerts.getByMountain - Get alerts for specific mountain
Reports
GET /api/trpc/reports.getAll - Get all reports
GET /api/trpc/reports.getByUser - Get user's reports (protected)
POST /api/trpc/reports.create - Create new report (protected)
POST /api/trpc/reports.updateStatus - Update report status (protected)
Files
GET /api/trpc/files.getByReport - Get files for report
GET /api/trpc/files.getByUser - Get user's files (protected)
POST /api/trpc/files.create - Upload file (protected)
Authentication
GET /api/trpc/auth.me - Get current user
POST /api/trpc/auth.logout - Logout user
Installation & Setup
Prerequisites
Node.js 22.13.0+
pnpm 10.4.1+
MySQL database
AWS S3 bucket for file storage
Environment Variables
Plain Text
DATABASE_URL=mysql://user:password@host:port/database
JWT_SECRET=your_jwt_secret
VITE_APP_ID=your_app_id
OAUTH_SERVER_URL=https://api.manus.im
VITE_OAUTH_PORTAL_URL=https://portal.manus.im
VITE_FRONTEND_FORGE_API_KEY=your_api_key
VITE_FRONTEND_FORGE_API_URL=https://api.manus.im
Installation Steps
Bash
# Install dependencies
pnpm install

# Push database migrations
pnpm db:push

# Run development server
pnpm dev

# Run tests
pnpm test

# Build for production
pnpm build

# Start production server
pnpm start
Project Structure
Plain Text
tsh_app/
├── client/                 # Frontend React application
│   ├── src/
│   │   ├── pages/         # Page components
│   │   ├── components/    # Reusable UI components
│   │   ├── lib/           # Utilities and helpers
│   │   ├── App.tsx        # Main app component
│   │   └── index.css      # Global styles
│   └── public/            # Static assets
├── server/                # Backend Node.js application
│   ├── routers.ts         # tRPC route definitions
│   ├── db.ts              # Database query functions
│   ├── storage.ts         # S3 file storage helpers
│   └── _core/             # Core framework files
├── drizzle/               # Database schema and migrations
│   ├── schema.ts          # Table definitions
│   └── migrations/        # Migration files
├── shared/                # Shared types and constants
└── package.json           # Project dependencies
Design System
Color Palette
Primary: #2d5a4f (Dark Green )
Secondary: #4a7c6f (Medium Green)
Accent: #6ba399 (Light Green)
Background: #ffffff (White)
Text: #1a1a1a (Dark Gray)
Typography
Display: Bold, 24-32px
Heading: Semi-bold, 18-20px
Body: Regular, 14-16px
Caption: Regular, 12-13px
Components
Rounded corners: 12-24px (border-radius)
Spacing: 4px, 8px, 12px, 16px, 24px
Shadows: Subtle elevation effects
Icons: Lucide React (24px default)
Testing
Test Coverage
12 vitest tests covering API endpoints
Authentication flow tests
Database query tests
Report creation and management tests
Running Tests
Bash
pnpm test
Deployment
Production Build
Bash
pnpm build
Deployment Options
Manus Platform: Built-in hosting with custom domains
Docker: Containerized deployment
Traditional VPS: Node.js server deployment
Security Features
OAuth 2.0 authentication via Manus
JWT-based session management
Protected API endpoints (protectedProcedure)
SQL injection prevention via Drizzle ORM
CORS configuration
Secure file upload validation
Performance Optimizations
Server-side rendering ready
Code splitting with React lazy loading
Database query optimization
Caching strategies
Image optimization
Bundle size optimization
Future Enhancements
Real-time Updates: WebSocket integration for live alerts
Advanced Analytics: Dashboard with statistics and trends
Mobile App: Native iOS/Android applications
AI Predictions: Machine learning for hazard forecasting
Multi-language Support: Full Arabic, English, Urdu support
Push Notifications: Real-time alert notifications
Admin Dashboard: Comprehensive management interface
Integration APIs: Third-party service integrations
Support & Documentation
API Documentation: Available at /api/docs
GitHub Issues: Report bugs and feature requests
Email Support: support@tsh.gov.sa
Phone Support: +966-920-020-405
License
Proprietary - Saudi Arabia Government Project
Contact Information
Project Name: Tuwaiq Smart Shield (TSH)
Version: 1.0.0
Last Updated: December 2025
Maintained By: Saudi Arabia Ministry of Interior

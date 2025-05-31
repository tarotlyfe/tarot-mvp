# TarotLyfe Technical Context

## Technologies Used

### Frontend Stack
- **React 18+**: Modern React with concurrent features and hooks
- **Vite**: Fast build tool and development server
- **JavaScript (ES2022+)**: Modern JavaScript features, NO TypeScript per project requirements
- **Redux Toolkit**: State management with RTK Query for API calls
- **React Router**: Client-side routing and navigation
- **React Hook Form**: Form state management and validation
- **Framer Motion**: Animations and transitions for card draws and UI polish

### Styling & Design
- **Tailwind CSS**: Utility-first CSS framework with custom design system
- **Custom CSS Variables**: Design tokens for colors, spacing, typography
- **Responsive Design**: Mobile-first approach with breakpoint system
- **Dark/Light Themes**: Theme switching with CSS custom properties

### Backend Stack
- **Node.js**: JavaScript runtime for server-side development
- **Express.js**: Web framework for RESTful API development
- **PostgreSQL**: Primary database for user data, readings, journals
- **Prisma**: Database ORM for schema management and queries
- **Redis**: Caching layer for sessions, API responses, and rate limiting
- **JWT**: Authentication tokens with refresh token rotation

### AI & External Services
- **OpenAI GPT-4**: AI-powered tarot interpretations and journaling prompts
- **Stripe**: Payment processing and subscription management
- **AWS S3**: File storage for user uploads and exports

### Desktop Application
- **Electron**: Cross-platform desktop app framework
- **SQLite**: Local database for offline functionality
- **IPC (Inter-Process Communication)**: Communication between main and renderer processes

### Testing Framework
- **Jest**: Unit testing for both frontend and backend
- **React Testing Library**: Component testing with user-centric approach
- **Cypress**: End-to-end testing for critical user flows
- **Supertest**: API endpoint testing

## Development Setup

### Prerequisites
- Node.js 18+ (LTS recommended)
- PostgreSQL 14+
- Redis 6+
- Git for version control

### Environment Configuration
```bash
# Frontend (.env.local)
VITE_API_URL=http://localhost:3001/api/v1
VITE_STRIPE_PUBLISHABLE_KEY=pk_test_...

# Backend (.env)
DATABASE_URL=postgresql://user:password@localhost:5432/tarotlyfe
REDIS_URL=redis://localhost:6379
JWT_SECRET=your-jwt-secret
JWT_REFRESH_SECRET=your-refresh-secret
OPENAI_API_KEY=sk-...
STRIPE_SECRET_KEY=sk_test_...
STRIPE_WEBHOOK_SECRET=whsec_...
```

### Development Commands
```bash
# Frontend development
cd frontend
npm install
npm run dev          # Start development server
npm run build        # Production build
npm run test         # Run tests
npm run lint         # ESLint checking

# Backend development
cd backend
npm install
npm run dev          # Start with nodemon
npm run start        # Production start
npm run test         # Run tests
npm run db:migrate   # Run database migrations
npm run db:seed      # Seed development data
```

### Database Setup
```bash
# PostgreSQL setup
createdb tarotlyfe_dev
createdb tarotlyfe_test

# Prisma setup
npx prisma migrate dev
npx prisma generate
npx prisma studio    # Database GUI
```

## Technical Constraints

### Performance Requirements
- **Page Load Time**: < 3 seconds for initial load
- **API Response Time**: < 500ms for most endpoints
- **Database Queries**: Optimized with proper indexing
- **Bundle Size**: Frontend bundle < 1MB gzipped

### Browser Support
- **Modern Browsers**: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- **Mobile Browsers**: iOS Safari 14+, Chrome Mobile 90+
- **No IE Support**: Focus on modern web standards

### Security Requirements
- **HTTPS Only**: All production traffic encrypted
- **CORS Configuration**: Restricted to allowed origins
- **Input Validation**: Server-side validation for all inputs
- **Rate Limiting**: API endpoints protected against abuse
- **SQL Injection Prevention**: Parameterized queries via Prisma

### Scalability Considerations
- **Horizontal Scaling**: Stateless backend design
- **Database Connection Pooling**: Efficient connection management
- **Caching Strategy**: Redis for frequently accessed data
- **CDN Ready**: Static assets optimized for CDN delivery

## Dependencies

### Frontend Dependencies
```json
{
  "react": "^18.2.0",
  "react-dom": "^18.2.0",
  "react-router-dom": "^6.8.0",
  "@reduxjs/toolkit": "^1.9.0",
  "react-redux": "^8.0.0",
  "react-hook-form": "^7.43.0",
  "framer-motion": "^10.0.0",
  "tailwindcss": "^3.2.0"
}
```

### Backend Dependencies
```json
{
  "express": "^4.18.0",
  "prisma": "^4.10.0",
  "@prisma/client": "^4.10.0",
  "jsonwebtoken": "^9.0.0",
  "bcryptjs": "^2.4.0",
  "redis": "^4.6.0",
  "stripe": "^11.0.0",
  "openai": "^3.2.0"
}
```

### Development Dependencies
```json
{
  "jest": "^29.0.0",
  "@testing-library/react": "^14.0.0",
  "cypress": "^12.0.0",
  "eslint": "^8.0.0",
  "prettier": "^2.8.0",
  "nodemon": "^2.0.0"
}
```

## Tool Usage Patterns

### Code Quality Tools
- **ESLint**: JavaScript linting with React and accessibility rules
- **Prettier**: Code formatting with consistent style
- **Husky**: Git hooks for pre-commit quality checks
- **lint-staged**: Run linters on staged files only

### Development Tools
- **VS Code**: Recommended IDE with extensions for React, Tailwind
- **Postman/Insomnia**: API testing and documentation
- **Prisma Studio**: Database management GUI
- **Redux DevTools**: State debugging and time-travel debugging

### Monitoring & Debugging
- **Console Logging**: Structured logging with different levels
- **Error Boundaries**: React error catching and reporting
- **Source Maps**: Debugging support in production
- **Performance Profiling**: React DevTools Profiler

## API Design Patterns

### RESTful Conventions
- **GET**: Retrieve data (idempotent)
- **POST**: Create new resources
- **PUT**: Update entire resources
- **PATCH**: Partial resource updates
- **DELETE**: Remove resources

### Response Format
```json
{
  "success": true,
  "data": { /* response data */ },
  "message": "Operation completed successfully",
  "timestamp": "2025-01-01T00:00:00Z"
}
```

### Error Response Format
```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input provided",
    "details": { /* field-specific errors */ }
  },
  "timestamp": "2025-01-01T00:00:00Z"
}
```

### Authentication Headers
```
Authorization: Bearer <jwt_token>
X-Refresh-Token: <refresh_token>
```

## Deployment Architecture

### Production Environment
- **Frontend**: Static hosting (Vercel/Netlify)
- **Backend**: Node.js server (Railway/Heroku)
- **Database**: Managed PostgreSQL (Railway/Heroku Postgres)
- **Cache**: Managed Redis (Railway/Heroku Redis)
- **Storage**: AWS S3 for file uploads

### Environment Variables Management
- **Development**: .env files (gitignored)
- **Production**: Platform-specific environment configuration
- **Secrets**: Encrypted storage for sensitive values

### CI/CD Pipeline
- **GitHub Actions**: Automated testing and deployment
- **Testing**: Run full test suite on pull requests
- **Deployment**: Automatic deployment on main branch merge
- **Rollback**: Quick rollback capability for failed deployments

## Performance Optimization

### Frontend Optimization
- **Code Splitting**: Route-based lazy loading with React.lazy()
- **Bundle Analysis**: Webpack Bundle Analyzer for size optimization
- **Image Optimization**: WebP format with fallbacks
- **Caching**: Service worker for offline functionality

### Backend Optimization
- **Database Indexing**: Optimized queries for frequent operations
- **Connection Pooling**: Prisma connection pool configuration
- **Response Compression**: Gzip compression middleware
- **API Caching**: Redis caching for expensive operations

### Monitoring
- **Performance Metrics**: Core Web Vitals tracking
- **Error Tracking**: Centralized error logging
- **Uptime Monitoring**: Health check endpoints
- **Analytics**: User behavior and performance analytics

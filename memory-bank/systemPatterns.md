# TarotLyfe System Patterns

## System Architecture

### Frontend Architecture
- **React 18+ with Vite**: Modern build tooling for fast development and optimized production builds
- **Component-Based Design**: Atomic design principles with reusable UI components
- **State Management**: Redux Toolkit for global state, React Hook Form for form state
- **Routing**: React Router for client-side navigation
- **Styling**: Tailwind CSS with custom design system integration

### Backend Architecture
- **Node.js + Express.js**: RESTful API with middleware-based request processing
- **Database Layer**: PostgreSQL for primary data, Redis for caching and sessions
- **Authentication**: JWT with refresh tokens, secure HTTP-only cookies
- **AI Integration**: OpenAI GPT-4 for tarot interpretations and journaling prompts
- **Payment Processing**: Stripe for subscription management

### Desktop Application
- **Electron Framework**: Cross-platform desktop app (Windows, macOS, Linux)
- **Offline Capabilities**: SQLite for local data storage and sync
- **Performance Optimization**: Preload scripts and efficient IPC communication

## Key Technical Decisions

### Data Flow Patterns
1. **Unidirectional Data Flow**: Redux actions → reducers → UI updates
2. **API-First Design**: Backend APIs designed for both web and desktop consumption
3. **Optimistic Updates**: UI updates immediately, with rollback on API failure
4. **Caching Strategy**: Redis for session data, browser cache for static assets

### Security Patterns
- **Authentication Flow**: JWT access tokens (15min) + refresh tokens (7 days)
- **Authorization**: Role-based access control (user, admin)
- **Data Protection**: Encryption at rest, HTTPS in transit
- **Input Validation**: Server-side validation with client-side feedback

### AI Integration Patterns
- **Contextual Prompts**: AI considers user history, current mood, and card context
- **Fallback Mechanisms**: Default interpretations when AI service unavailable
- **Rate Limiting**: Prevent AI service abuse and manage costs
- **Response Caching**: Cache AI responses for identical contexts

## Design Patterns in Use

### Frontend Patterns
- **Container/Presentational Components**: Separation of logic and UI
- **Custom Hooks**: Reusable stateful logic (useAuth, useTarotReading, useJournal)
- **Higher-Order Components**: Cross-cutting concerns (authentication, error boundaries)
- **Render Props**: Flexible component composition for complex UI states

### Backend Patterns
- **Middleware Pattern**: Request processing pipeline (auth, validation, logging)
- **Repository Pattern**: Data access abstraction layer
- **Service Layer**: Business logic separation from controllers
- **Event-Driven Architecture**: Webhook handling for payments and notifications

### Database Patterns
- **Normalized Schema**: Efficient data storage with proper relationships
- **Soft Deletes**: Preserve user data for recovery and analytics
- **Audit Logging**: Track changes for security and debugging
- **Connection Pooling**: Efficient database connection management

## Component Relationships

### Core Components Hierarchy
```
App
├── AuthProvider (Context)
├── Router
│   ├── PublicRoutes
│   │   ├── Landing
│   │   ├── Login
│   │   └── Register
│   └── ProtectedRoutes
│       ├── Dashboard
│       ├── TarotReading
│       ├── Journal
│       ├── Analytics
│       └── Settings
```

### State Management Structure
```
Redux Store
├── auth (user session, tokens)
├── tarot (current reading, card history)
├── journal (entries, drafts, prompts)
├── mood (tracking data, trends)
├── subscription (tier, status, features)
└── ui (loading states, modals, notifications)
```

### API Endpoint Structure
```
/api/v1
├── /auth (login, register, refresh)
├── /users (profile, preferences)
├── /tarot (readings, cards, interpretations)
├── /journal (entries, prompts, tags)
├── /mood (tracking, analytics)
├── /subscription (plans, billing, webhooks)
└── /admin (user management, analytics)
```

## Critical Implementation Paths

### User Authentication Flow
1. User submits credentials → Frontend validation
2. API validates credentials → JWT generation
3. Tokens stored in HTTP-only cookies → Redux state update
4. Protected routes check auth state → Redirect if unauthorized
5. Token refresh on expiry → Seamless user experience

### Tarot Reading Flow
1. User initiates reading → Loading state activated
2. Backend generates random card selection → Database logging
3. AI service generates interpretation → Fallback if unavailable
4. Frontend displays cards with animation → State persistence
5. User can save or share reading → Journal integration prompt

### Journaling Integration Flow
1. User starts journal entry → Auto-save timer begins
2. AI generates contextual prompts → User can accept/modify
3. Rich-text editor saves content → Real-time sync
4. Entry linked to tarot reading → Relationship stored
5. Tags suggested and applied → Search indexing

### Subscription Management Flow
1. User selects plan → Stripe checkout initiated
2. Payment processed → Webhook confirms success
3. Database updated → Feature access granted
4. Frontend state refreshed → UI reflects new permissions
5. Billing cycle managed → Automated renewals/failures

## Performance Optimization Patterns

### Frontend Optimization
- **Code Splitting**: Route-based lazy loading
- **Memoization**: React.memo for expensive components
- **Virtual Scrolling**: Large lists (journal entries, card history)
- **Image Optimization**: WebP format with fallbacks

### Backend Optimization
- **Database Indexing**: Query optimization for frequent operations
- **Response Caching**: Redis for repeated API calls
- **Connection Pooling**: Efficient database connections
- **Compression**: Gzip for API responses

### Desktop App Optimization
- **Preload Scripts**: Faster startup times
- **Background Sync**: Offline-first with sync when online
- **Memory Management**: Efficient Electron process handling
- **Native Integrations**: OS-specific optimizations

## Error Handling Patterns

### Frontend Error Handling
- **Error Boundaries**: Catch React component errors
- **Global Error Handler**: Centralized error logging
- **User-Friendly Messages**: Technical errors translated to user language
- **Retry Mechanisms**: Automatic retry for transient failures

### Backend Error Handling
- **Structured Logging**: Consistent error format
- **Error Middleware**: Centralized error processing
- **Graceful Degradation**: Fallbacks for service failures
- **Health Checks**: Monitoring and alerting

### Data Integrity Patterns
- **Transaction Management**: ACID compliance for critical operations
- **Validation Layers**: Client and server-side validation
- **Backup Strategies**: Regular data backups and recovery procedures
- **Conflict Resolution**: Handling concurrent data modifications

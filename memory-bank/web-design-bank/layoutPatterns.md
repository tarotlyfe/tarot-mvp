# TarotLyfe Layout Patterns

## Grid System

### 12-Column Responsive Grid
The TarotLyfe platform uses a flexible 12-column grid system that adapts seamlessly across all device sizes, ensuring consistent spacing and alignment while maintaining visual hierarchy.

#### Grid Specifications
- **Base Unit**: 4px (0.25rem)
- **Column Count**: 12 columns
- **Gutter Width**: 24px (1.5rem) on desktop, 16px (1rem) on mobile
- **Max Width**: 1440px (90rem) for large screens
- **Container Padding**: 24px (1.5rem) on desktop, 16px (1rem) on mobile

#### Grid Implementation
```css
.container {
  max-width: 1440px;
  margin: 0 auto;
  padding: 0 1.5rem;
}

.grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 1.5rem;
}

@media (max-width: 768px) {
  .container {
    padding: 0 1rem;
  }
  
  .grid {
    gap: 1rem;
  }
}
```

### Responsive Breakpoints

#### Mobile First Approach
All layouts start with mobile design and progressively enhance for larger screens.

#### Breakpoint Definitions
- **Mobile**: 320px - 767px (sm)
- **Tablet**: 768px - 1023px (md)
- **Desktop**: 1024px - 1439px (lg)
- **Large Desktop**: 1440px+ (xl)

#### Tailwind Breakpoint Configuration
```javascript
screens: {
  'sm': '640px',   // Mobile landscape
  'md': '768px',   // Tablet
  'lg': '1024px',  // Desktop
  'xl': '1280px',  // Large desktop
  '2xl': '1536px'  // Extra large
}
```

#### Column Behavior by Breakpoint
- **Mobile (sm)**: 1-2 columns, full-width cards
- **Tablet (md)**: 2-3 columns, medium cards
- **Desktop (lg)**: 3-4 columns, standard cards
- **Large (xl)**: 4-6 columns, compact cards

## Section Blueprints

### Hero Section Layout

#### Primary Hero (Landing Page)
```html
<section class="hero-primary">
  <div class="container">
    <div class="grid grid-cols-12 gap-6 items-center min-h-screen">
      <!-- Content Column -->
      <div class="col-span-12 lg:col-span-6 order-2 lg:order-1">
        <h1 class="hero-title">Discover Your Path</h1>
        <p class="hero-subtitle">AI-powered tarot readings and journaling</p>
        <div class="hero-actions">
          <button class="btn-primary">Start Your Journey</button>
          <button class="btn-secondary">Learn More</button>
        </div>
      </div>
      
      <!-- Visual Column -->
      <div class="col-span-12 lg:col-span-6 order-1 lg:order-2">
        <div class="hero-visual">
          <!-- Tarot card display or mystical imagery -->
        </div>
      </div>
    </div>
  </div>
</section>
```

#### Dashboard Hero
```html
<section class="hero-dashboard">
  <div class="container">
    <div class="grid grid-cols-12 gap-6">
      <!-- Welcome Message -->
      <div class="col-span-12 md:col-span-8">
        <h1 class="dashboard-welcome">Welcome back, [Name]</h1>
        <p class="dashboard-subtitle">Continue your spiritual journey</p>
      </div>
      
      <!-- Quick Actions -->
      <div class="col-span-12 md:col-span-4">
        <div class="quick-actions">
          <button class="btn-primary">Draw a Card</button>
          <button class="btn-secondary">Journal Entry</button>
        </div>
      </div>
    </div>
  </div>
</section>
```

### Card Layouts

#### Tarot Card Display Patterns

##### Single Card Layout
```html
<div class="card-single-container">
  <div class="card-single">
    <div class="card-image-wrapper">
      <img src="card-image.jpg" alt="Card Name" class="card-image" />
      <div class="card-overlay">
        <h3 class="card-name">The Fool</h3>
      </div>
    </div>
    <div class="card-content">
      <h4 class="card-title">Your Card Today</h4>
      <p class="card-interpretation">AI-generated interpretation...</p>
      <div class="card-actions">
        <button class="btn-secondary">Journal About This</button>
        <button class="btn-ghost">Save Reading</button>
      </div>
    </div>
  </div>
</div>
```

##### Three Card Spread Layout
```html
<div class="spread-three-container">
  <div class="spread-header">
    <h3 class="spread-title">Past, Present, Future</h3>
    <p class="spread-description">Explore your journey through time</p>
  </div>
  
  <div class="spread-cards">
    <div class="card-position">
      <div class="card-wrapper">
        <img src="past-card.jpg" alt="Past Card" class="card-image" />
      </div>
      <div class="card-label">Past</div>
    </div>
    
    <div class="card-position featured">
      <div class="card-wrapper">
        <img src="present-card.jpg" alt="Present Card" class="card-image" />
      </div>
      <div class="card-label">Present</div>
    </div>
    
    <div class="card-position">
      <div class="card-wrapper">
        <img src="future-card.jpg" alt="Future Card" class="card-image" />
      </div>
      <div class="card-label">Future</div>
    </div>
  </div>
  
  <div class="spread-interpretation">
    <h4 class="interpretation-title">Your Reading</h4>
    <div class="interpretation-content">
      <!-- AI-generated interpretation -->
    </div>
  </div>
</div>
```

#### Journal Entry Cards
```html
<div class="journal-card">
  <div class="journal-header">
    <div class="journal-date">Today, 3:42 PM</div>
    <div class="journal-mood">
      <span class="mood-indicator mood-peaceful"></span>
      Peaceful
    </div>
  </div>
  
  <div class="journal-content">
    <h4 class="journal-title">Reflection on The Star</h4>
    <p class="journal-excerpt">Today's card brought me hope...</p>
  </div>
  
  <div class="journal-footer">
    <div class="journal-tags">
      <span class="tag">hope</span>
      <span class="tag">guidance</span>
    </div>
    <button class="btn-ghost">Continue Reading</button>
  </div>
</div>
```

#### Dashboard Widget Cards
```html
<div class="widget-card">
  <div class="widget-header">
    <h4 class="widget-title">Recent Insights</h4>
    <button class="widget-action">View All</button>
  </div>
  
  <div class="widget-content">
    <!-- Widget-specific content -->
  </div>
</div>
```

### Form Patterns

#### Authentication Forms

##### Registration Form Layout
```html
<div class="auth-container">
  <div class="auth-card">
    <div class="auth-header">
      <h2 class="auth-title">Begin Your Journey</h2>
      <p class="auth-subtitle">Create your TarotLyfe account</p>
    </div>
    
    <form class="auth-form">
      <div class="form-group">
        <label for="email" class="form-label">Email</label>
        <input type="email" id="email" class="form-input" />
      </div>
      
      <div class="form-group">
        <label for="password" class="form-label">Password</label>
        <input type="password" id="password" class="form-input" />
      </div>
      
      <div class="form-group">
        <label for="confirm-password" class="form-label">Confirm Password</label>
        <input type="password" id="confirm-password" class="form-input" />
      </div>
      
      <button type="submit" class="btn-primary btn-full">Create Account</button>
    </form>
    
    <div class="auth-footer">
      <p class="auth-link">Already have an account? <a href="/login">Sign in</a></p>
    </div>
  </div>
</div>
```

##### Login Form Layout
```html
<div class="auth-container">
  <div class="auth-card">
    <div class="auth-header">
      <h2 class="auth-title">Welcome Back</h2>
      <p class="auth-subtitle">Continue your spiritual journey</p>
    </div>
    
    <form class="auth-form">
      <div class="form-group">
        <label for="email" class="form-label">Email</label>
        <input type="email" id="email" class="form-input" />
      </div>
      
      <div class="form-group">
        <label for="password" class="form-label">Password</label>
        <input type="password" id="password" class="form-input" />
        <a href="/forgot-password" class="form-link">Forgot password?</a>
      </div>
      
      <button type="submit" class="btn-primary btn-full">Sign In</button>
    </form>
    
    <div class="auth-divider">
      <span>or</span>
    </div>
    
    <button class="btn-secondary btn-full">
      <svg class="btn-icon"><!-- Google icon --></svg>
      Continue with Google
    </button>
    
    <div class="auth-footer">
      <p class="auth-link">New to TarotLyfe? <a href="/register">Create account</a></p>
    </div>
  </div>
</div>
```

#### Journaling Interface Layout
```html
<div class="journal-editor-container">
  <div class="journal-editor">
    <div class="editor-header">
      <div class="editor-meta">
        <input type="text" placeholder="Entry title..." class="title-input" />
        <div class="editor-tools">
          <button class="tool-btn">Bold</button>
          <button class="tool-btn">Italic</button>
          <button class="tool-btn">List</button>
        </div>
      </div>
    </div>
    
    <div class="editor-content">
      <textarea placeholder="What insights are emerging for you today?" class="editor-textarea"></textarea>
    </div>
    
    <div class="editor-sidebar">
      <div class="sidebar-section">
        <h4 class="sidebar-title">Today's Card</h4>
        <div class="card-reference">
          <img src="card-thumb.jpg" alt="Card" class="card-thumb" />
          <div class="card-info">
            <h5 class="card-name">The Star</h5>
            <p class="card-keywords">Hope, Guidance, Inspiration</p>
          </div>
        </div>
      </div>
      
      <div class="sidebar-section">
        <h4 class="sidebar-title">Reflection Prompts</h4>
        <div class="prompts-list">
          <button class="prompt-btn">How does this card relate to your current situation?</button>
          <button class="prompt-btn">What emotions does this card evoke?</button>
          <button class="prompt-btn">What action might this card be encouraging?</button>
        </div>
      </div>
    </div>
    
    <div class="editor-footer">
      <div class="editor-actions">
        <button class="btn-ghost">Save Draft</button>
        <button class="btn-primary">Publish Entry</button>
      </div>
    </div>
  </div>
</div>
```

### Navigation Patterns

#### Header Navigation
```html
<header class="site-header">
  <div class="container">
    <div class="header-content">
      <!-- Logo -->
      <div class="header-logo">
        <a href="/" class="logo-link">
          <img src="logo.svg" alt="TarotLyfe" class="logo" />
        </a>
      </div>
      
      <!-- Main Navigation -->
      <nav class="header-nav">
        <ul class="nav-list">
          <li class="nav-item">
            <a href="/dashboard" class="nav-link">Dashboard</a>
          </li>
          <li class="nav-item">
            <a href="/readings" class="nav-link">Readings</a>
          </li>
          <li class="nav-item">
            <a href="/journal" class="nav-link">Journal</a>
          </li>
          <li class="nav-item">
            <a href="/insights" class="nav-link">Insights</a>
          </li>
        </ul>
      </nav>
      
      <!-- User Actions -->
      <div class="header-actions">
        <button class="theme-toggle" aria-label="Toggle theme">
          <svg class="theme-icon"><!-- Theme icon --></svg>
        </button>
        <div class="user-menu">
          <button class="user-avatar">
            <img src="avatar.jpg" alt="User" class="avatar-image" />
          </button>
          <!-- Dropdown menu -->
        </div>
      </div>
      
      <!-- Mobile Menu Toggle -->
      <button class="mobile-menu-toggle md:hidden">
        <svg class="menu-icon"><!-- Hamburger icon --></svg>
      </button>
    </div>
  </div>
</header>
```

#### Sidebar Navigation (Dashboard)
```html
<aside class="dashboard-sidebar">
  <div class="sidebar-content">
    <!-- Primary Navigation -->
    <nav class="sidebar-nav">
      <ul class="nav-list">
        <li class="nav-item">
          <a href="/dashboard" class="nav-link active">
            <svg class="nav-icon"><!-- Dashboard icon --></svg>
            Dashboard
          </a>
        </li>
        <li class="nav-item">
          <a href="/draw-card" class="nav-link">
            <svg class="nav-icon"><!-- Card icon --></svg>
            Draw Card
          </a>
        </li>
        <li class="nav-item">
          <a href="/journal" class="nav-link">
            <svg class="nav-icon"><!-- Journal icon --></svg>
            Journal
          </a>
        </li>
        <li class="nav-item">
          <a href="/readings" class="nav-link">
            <svg class="nav-icon"><!-- History icon --></svg>
            Past Readings
          </a>
        </li>
        <li class="nav-item">
          <a href="/insights" class="nav-link">
            <svg class="nav-icon"><!-- Insights icon --></svg>
            Insights
          </a>
        </li>
      </ul>
    </nav>
    
    <!-- Secondary Navigation -->
    <div class="sidebar-secondary">
      <div class="subscription-widget">
        <h4 class="widget-title">Upgrade to Premium</h4>
        <p class="widget-text">Unlock advanced features</p>
        <button class="btn-accent btn-sm">Learn More</button>
      </div>
    </div>
  </div>
</aside>
```

#### Mobile Menu
```html
<div class="mobile-menu" data-state="closed">
  <div class="mobile-menu-overlay"></div>
  <div class="mobile-menu-content">
    <div class="mobile-menu-header">
      <div class="mobile-logo">
        <img src="logo.svg" alt="TarotLyfe" class="logo" />
      </div>
      <button class="mobile-menu-close">
        <svg class="close-icon"><!-- Close icon --></svg>
      </button>
    </div>
    
    <nav class="mobile-nav">
      <ul class="mobile-nav-list">
        <li class="mobile-nav-item">
          <a href="/dashboard" class="mobile-nav-link">Dashboard</a>
        </li>
        <li class="mobile-nav-item">
          <a href="/draw-card" class="mobile-nav-link">Draw Card</a>
        </li>
        <li class="mobile-nav-item">
          <a href="/journal" class="mobile-nav-link">Journal</a>
        </li>
        <li class="mobile-nav-item">
          <a href="/readings" class="mobile-nav-link">Past Readings</a>
        </li>
        <li class="mobile-nav-item">
          <a href="/insights" class="mobile-nav-link">Insights</a>
        </li>
      </ul>
    </nav>
    
    <div class="mobile-menu-footer">
      <div class="user-info">
        <img src="avatar.jpg" alt="User" class="user-avatar" />
        <div class="user-details">
          <h4 class="user-name">Sarah Johnson</h4>
          <p class="user-email">sarah@example.com</p>
        </div>
      </div>
      <button class="btn-ghost btn-full">Sign Out</button>
    </div>
  </div>
</div>
```

## Gestalt Principles Implementation

### Proximity
Group related elements together to create clear relationships and reduce cognitive load.

#### Content Grouping
- **Card Information**: Image, title, and interpretation grouped together
- **Form Fields**: Related inputs grouped with consistent spacing
- **Navigation Items**: Primary and secondary navigation clearly separated
- **Action Buttons**: Related actions grouped with primary action emphasized

#### Spacing Hierarchy
```css
/* Tight grouping for related elements */
.related-group {
  gap: 0.5rem; /* 8px */
}

/* Medium spacing for section separation */
.section-spacing {
  gap: 1.5rem; /* 24px */
}

/* Large spacing for major section breaks */
.major-spacing {
  gap: 3rem; /* 48px */
}
```

### Similarity
Use consistent visual elements to indicate similar functionality and create cohesive experience.

#### Visual Consistency
- **Button Styles**: Consistent styling for similar actions across the platform
- **Card Layouts**: Uniform card structure for different content types
- **Typography**: Consistent text hierarchy and styling
- **Color Usage**: Systematic color application for different element types

#### Pattern Consistency
```css
/* Consistent card pattern */
.card-base {
  @apply rounded-lg border bg-card text-card-foreground shadow-sm p-6;
}

/* Consistent button pattern */
.btn-base {
  @apply inline-flex items-center justify-center rounded-md text-sm font-medium transition-colors;
}
```

### Closure
Use visual elements that suggest completion and create satisfying user experiences.

#### Visual Completion
- **Progress Indicators**: Clear progress through multi-step processes
- **Loading States**: Smooth transitions that indicate completion
- **Form Validation**: Clear success and error states
- **Card Animations**: Smooth reveal animations for tarot cards

#### Interaction Feedback
```css
/* Smooth transitions for completion feedback */
.completion-feedback {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

/* Success state styling */
.success-state {
  @apply border-sage-500 bg-sage-50 text-sage-700;
}
```

### Figure/Ground
Create clear visual hierarchy through contrast and layering.

#### Layering Strategy
- **Background**: Subtle, non-distracting base layer
- **Content**: Clear, high-contrast content layer
- **Interactive Elements**: Elevated elements with shadows and hover states
- **Overlays**: Modal and dropdown overlays with proper backdrop

#### Contrast Implementation
```css
/* High contrast for primary content */
.primary-content {
  @apply bg-background text-foreground;
}

/* Subtle contrast for secondary content */
.secondary-content {
  @apply bg-muted text-muted-foreground;
}

/* Elevated elements */
.elevated {
  @apply shadow-medium bg-card;
}
```

### Continuation
Guide user attention through visual flow and directional elements.

#### Visual Flow
- **Reading Path**: Left-to-right, top-to-bottom content flow
- **Action Sequences**: Clear progression through user journeys
- **Navigation Flow**: Logical navigation hierarchy and breadcrumbs
- **Content Relationships**: Visual connections between related content

#### Directional Elements
```css
/* Subtle directional indicators */
.flow-indicator {
  position: relative;
}

.flow-indicator::after {
  content: '';
  position: absolute;
  /* Arrow or line styling */
}
```

## Responsive Layout Strategies

### Mobile-First Approach
Start with mobile design and progressively enhance for larger screens.

#### Mobile Layout Priorities
1. **Single Column**: Stack content vertically for easy scanning
2. **Touch Targets**: Minimum 44px touch targets for accessibility
3. **Readable Text**: Minimum 16px font size for body text
4. **Simplified Navigation**: Collapsible menu with clear hierarchy

#### Progressive Enhancement
```css
/* Mobile base styles */
.responsive-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
}

/* Tablet enhancement */
@media (min-width: 768px) {
  .responsive-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 1.5rem;
  }
}

/* Desktop enhancement */
@media (min-width: 1024px) {
  .responsive-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
  }
}
```

### Content Adaptation
Ensure content remains accessible and usable across all device sizes.

#### Text Scaling
- **Headings**: Scale proportionally with viewport size
- **Body Text**: Maintain readability at all sizes
- **UI Text**: Consistent sizing for interface elements

#### Image Handling
- **Responsive Images**: Serve appropriate sizes for device capabilities
- **Art Direction**: Different crops/compositions for different screen sizes
- **Performance**: Optimize loading for mobile connections

### Interaction Adaptation
Adapt interactions for different input methods and screen sizes.

#### Touch vs. Mouse
- **Touch Targets**: Larger targets for touch interfaces
- **Hover States**: Graceful degradation for touch devices
- **Gestures**: Support for swipe and pinch gestures where appropriate

#### Keyboard Navigation
- **Focus Management**: Clear focus indicators and logical tab order
- **Shortcuts**: Keyboard shortcuts for power users
- **Accessibility**: Full keyboard accessibility for all features

---

**Document Status**: Complete  
**Last Updated**: 2025-05-30  
**Next Review**: After Phase 1 completion  
**Related Documents**: styleGuide.md, brandContext.md, componentLibrary.md

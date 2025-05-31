# TarotLyfe Component Library

## Component Architecture

### Atomic Design Principles
The TarotLyfe component library follows atomic design methodology, organizing components into a clear hierarchy that promotes reusability, consistency, and maintainability.

#### Component Hierarchy
- **Atoms**: Basic building blocks (buttons, inputs, icons)
- **Molecules**: Simple combinations of atoms (form fields, card headers)
- **Organisms**: Complex UI sections (navigation, forms, card layouts)
- **Templates**: Page-level layouts and structures
- **Pages**: Specific instances of templates with real content

#### Design Token Integration
All components utilize design tokens from the Tailwind configuration, ensuring consistent theming and easy maintenance across the entire platform.

## Button Components

### Primary Button
The primary button is used for the most important actions on a page.

#### Variants
```jsx
// Primary Button - Main call-to-action
<button className="btn btn-primary">
  Start Your Journey
</button>

// Primary with Icon
<button className="btn btn-primary">
  <svg className="btn-icon"><!-- Icon --></svg>
  Draw a Card
</button>

// Primary Loading State
<button className="btn btn-primary" disabled>
  <svg className="btn-spinner"><!-- Spinner --></svg>
  Loading...
</button>
```

#### Styling
```css
.btn-primary {
  @apply bg-primary text-primary-foreground hover:bg-primary/90 
         focus-visible:ring-primary shadow-sm;
}

.btn-primary:disabled {
  @apply opacity-50 cursor-not-allowed;
}
```

#### Sizes
- **Small**: `h-8 px-3 text-xs` - For compact interfaces
- **Medium**: `h-10 px-4 text-sm` - Default size
- **Large**: `h-12 px-6 text-base` - For prominent actions

### Secondary Button
Secondary buttons are used for less important actions or as alternatives to primary actions.

#### Variants
```jsx
// Secondary Button
<button className="btn btn-secondary">
  Learn More
</button>

// Secondary Outline
<button className="btn btn-secondary-outline">
  Cancel
</button>
```

#### Styling
```css
.btn-secondary {
  @apply bg-secondary text-secondary-foreground hover:bg-secondary/80
         focus-visible:ring-secondary border border-input;
}

.btn-secondary-outline {
  @apply border border-input bg-background hover:bg-accent 
         hover:text-accent-foreground focus-visible:ring-ring;
}
```

### Ghost Button
Ghost buttons provide minimal visual weight while maintaining accessibility.

#### Usage
```jsx
// Ghost Button
<button className="btn btn-ghost">
  Skip for now
</button>

// Ghost with Icon
<button className="btn btn-ghost">
  <svg className="btn-icon"><!-- Icon --></svg>
  Settings
</button>
```

#### Styling
```css
.btn-ghost {
  @apply hover:bg-accent hover:text-accent-foreground
         focus-visible:ring-ring;
}
```

### Danger Button
Used for destructive actions that require user confirmation.

#### Usage
```jsx
// Danger Button
<button className="btn btn-danger">
  Delete Account
</button>
```

#### Styling
```css
.btn-danger {
  @apply bg-red-600 text-white hover:bg-red-700
         focus-visible:ring-red-500;
}
```

### Button Accessibility
- **Focus Management**: Clear focus indicators with ring styles
- **Keyboard Support**: Full keyboard navigation support
- **Screen Reader**: Proper ARIA labels and descriptions
- **Loading States**: Disabled state with loading indicators
- **Touch Targets**: Minimum 44px touch target size

## Input Components

### Text Input
Standard text input with validation states and accessibility features.

#### Basic Usage
```jsx
// Standard Text Input
<div className="form-group">
  <label htmlFor="email" className="form-label">
    Email Address
  </label>
  <input 
    type="email" 
    id="email" 
    className="form-input"
    placeholder="Enter your email"
  />
</div>
```

#### Validation States
```jsx
// Success State
<input className="form-input form-input-success" />

// Error State
<input className="form-input form-input-error" />
<p className="form-error">Please enter a valid email address</p>

// Warning State
<input className="form-input form-input-warning" />
<p className="form-warning">This email is already registered</p>
```

#### Styling
```css
.form-input {
  @apply flex h-10 w-full rounded-md border border-input 
         bg-background px-3 py-2 text-sm ring-offset-background
         file:border-0 file:bg-transparent file:text-sm file:font-medium
         placeholder:text-muted-foreground 
         focus-visible:outline-none focus-visible:ring-2 
         focus-visible:ring-ring focus-visible:ring-offset-2
         disabled:cursor-not-allowed disabled:opacity-50;
}

.form-input-success {
  @apply border-sage-500 focus-visible:ring-sage-500;
}

.form-input-error {
  @apply border-red-500 focus-visible:ring-red-500;
}

.form-input-warning {
  @apply border-amber-500 focus-visible:ring-amber-500;
}
```

### Password Input
Password input with visibility toggle and strength indicator.

#### Usage
```jsx
// Password Input with Toggle
<div className="form-group">
  <label htmlFor="password" className="form-label">
    Password
  </label>
  <div className="password-input-wrapper">
    <input 
      type={showPassword ? "text" : "password"}
      id="password" 
      className="form-input pr-10"
    />
    <button 
      type="button"
      className="password-toggle"
      onClick={() => setShowPassword(!showPassword)}
    >
      <svg className="password-icon">
        {showPassword ? <EyeOffIcon /> : <EyeIcon />}
      </svg>
    </button>
  </div>
  <div className="password-strength">
    <div className="strength-meter">
      <div className="strength-bar strength-weak"></div>
    </div>
    <p className="strength-text">Weak password</p>
  </div>
</div>
```

### Textarea
Multi-line text input for longer content.

#### Usage
```jsx
// Standard Textarea
<div className="form-group">
  <label htmlFor="journal-entry" className="form-label">
    Journal Entry
  </label>
  <textarea 
    id="journal-entry"
    className="form-textarea"
    rows={6}
    placeholder="What insights are emerging for you today?"
  />
</div>
```

#### Styling
```css
.form-textarea {
  @apply flex min-h-[80px] w-full rounded-md border border-input
         bg-background px-3 py-2 text-sm ring-offset-background
         placeholder:text-muted-foreground
         focus-visible:outline-none focus-visible:ring-2
         focus-visible:ring-ring focus-visible:ring-offset-2
         disabled:cursor-not-allowed disabled:opacity-50;
}
```

### Form Labels and Help Text
Consistent labeling and help text for all form elements.

#### Usage
```jsx
// Form Label
<label htmlFor="input-id" className="form-label">
  Field Label
  <span className="form-required">*</span>
</label>

// Help Text
<p className="form-help">
  This information helps us personalize your experience
</p>

// Error Message
<p className="form-error">
  <svg className="form-error-icon"><!-- Error icon --></svg>
  This field is required
</p>
```

#### Styling
```css
.form-label {
  @apply text-sm font-medium leading-none 
         peer-disabled:cursor-not-allowed peer-disabled:opacity-70;
}

.form-required {
  @apply text-red-500 ml-1;
}

.form-help {
  @apply text-sm text-muted-foreground mt-1;
}

.form-error {
  @apply text-sm text-red-600 mt-1 flex items-center gap-1;
}
```

## Card Components

### Base Card
The foundation card component used throughout the platform.

#### Basic Usage
```jsx
// Standard Card
<div className="card">
  <div className="card-header">
    <h3 className="card-title">Card Title</h3>
    <p className="card-description">Card description text</p>
  </div>
  <div className="card-content">
    <!-- Card content -->
  </div>
  <div className="card-footer">
    <button className="btn btn-primary">Action</button>
  </div>
</div>
```

#### Styling
```css
.card {
  @apply rounded-lg border bg-card text-card-foreground shadow-sm;
}

.card-header {
  @apply flex flex-col space-y-1.5 p-6;
}

.card-title {
  @apply text-2xl font-semibold leading-none tracking-tight;
}

.card-description {
  @apply text-sm text-muted-foreground;
}

.card-content {
  @apply p-6 pt-0;
}

.card-footer {
  @apply flex items-center p-6 pt-0;
}
```

### Tarot Card Component
Specialized card component for displaying tarot cards.

#### Usage
```jsx
// Tarot Card Display
<div className="tarot-card">
  <div className="tarot-card-image">
    <img 
      src="/cards/the-fool.jpg" 
      alt="The Fool"
      className="card-image"
    />
    <div className="card-overlay">
      <h3 className="card-name">The Fool</h3>
      <p className="card-number">0</p>
    </div>
  </div>
  <div className="tarot-card-content">
    <h4 className="card-meaning">New Beginnings</h4>
    <p className="card-keywords">Adventure, Potential, Freedom</p>
  </div>
</div>
```

#### Styling
```css
.tarot-card {
  @apply relative overflow-hidden rounded-xl bg-card shadow-medium
         transition-transform duration-200 hover:scale-105;
}

.tarot-card-image {
  @apply relative aspect-[2/3] overflow-hidden;
}

.card-image {
  @apply h-full w-full object-cover;
}

.card-overlay {
  @apply absolute inset-0 bg-gradient-to-t from-black/60 to-transparent
         flex flex-col justify-end p-4 text-white;
}

.card-name {
  @apply text-lg font-semibold;
}

.card-number {
  @apply text-sm opacity-80;
}

.tarot-card-content {
  @apply p-4;
}

.card-meaning {
  @apply font-medium text-foreground;
}

.card-keywords {
  @apply text-sm text-muted-foreground mt-1;
}
```

### Journal Card Component
Card component for displaying journal entries.

#### Usage
```jsx
// Journal Entry Card
<div className="journal-card">
  <div className="journal-card-header">
    <div className="journal-meta">
      <time className="journal-date">March 15, 2024</time>
      <div className="journal-mood">
        <span className="mood-indicator mood-peaceful"></span>
        Peaceful
      </div>
    </div>
    <button className="journal-menu">
      <svg className="menu-icon"><!-- Menu icon --></svg>
    </button>
  </div>
  
  <div className="journal-card-content">
    <h3 className="journal-title">Reflection on The Star</h3>
    <p className="journal-excerpt">
      Today's card brought me a sense of hope and renewal...
    </p>
  </div>
  
  <div className="journal-card-footer">
    <div className="journal-tags">
      <span className="tag">hope</span>
      <span className="tag">guidance</span>
      <span className="tag">renewal</span>
    </div>
    <button className="btn btn-ghost btn-sm">Read More</button>
  </div>
</div>
```

### Widget Card Component
Dashboard widget container with consistent styling.

#### Usage
```jsx
// Dashboard Widget
<div className="widget-card">
  <div className="widget-header">
    <h4 className="widget-title">Recent Insights</h4>
    <button className="widget-action">View All</button>
  </div>
  <div className="widget-content">
    <!-- Widget content -->
  </div>
</div>
```

## Modal Components

### Base Modal
Foundation modal component with backdrop and focus management.

#### Usage
```jsx
// Modal Component
<div className="modal-overlay" onClick={onClose}>
  <div className="modal-content" onClick={e => e.stopPropagation()}>
    <div className="modal-header">
      <h2 className="modal-title">Modal Title</h2>
      <button className="modal-close" onClick={onClose}>
        <svg className="close-icon"><!-- Close icon --></svg>
      </button>
    </div>
    
    <div className="modal-body">
      <!-- Modal content -->
    </div>
    
    <div className="modal-footer">
      <button className="btn btn-ghost" onClick={onClose}>
        Cancel
      </button>
      <button className="btn btn-primary" onClick={onConfirm}>
        Confirm
      </button>
    </div>
  </div>
</div>
```

#### Styling
```css
.modal-overlay {
  @apply fixed inset-0 z-50 bg-background/80 backdrop-blur-sm
         flex items-center justify-center p-4;
}

.modal-content {
  @apply relative bg-background border rounded-lg shadow-lg
         w-full max-w-lg max-h-[85vh] overflow-hidden;
}

.modal-header {
  @apply flex items-center justify-between p-6 border-b;
}

.modal-title {
  @apply text-lg font-semibold;
}

.modal-close {
  @apply rounded-sm opacity-70 ring-offset-background transition-opacity
         hover:opacity-100 focus:outline-none focus:ring-2 
         focus:ring-ring focus:ring-offset-2;
}

.modal-body {
  @apply p-6 overflow-y-auto;
}

.modal-footer {
  @apply flex justify-end gap-2 p-6 border-t;
}
```

### Confirmation Modal
Specialized modal for confirmation dialogs.

#### Usage
```jsx
// Confirmation Modal
<ConfirmationModal
  isOpen={isOpen}
  onClose={onClose}
  onConfirm={onConfirm}
  title="Delete Journal Entry"
  description="Are you sure you want to delete this journal entry? This action cannot be undone."
  confirmText="Delete"
  cancelText="Cancel"
  variant="danger"
/>
```

### Card Reading Modal
Modal for displaying detailed tarot card information.

#### Usage
```jsx
// Card Reading Modal
<CardReadingModal
  isOpen={isOpen}
  onClose={onClose}
  card={selectedCard}
  interpretation={aiInterpretation}
  onJournal={handleJournalAction}
  onSave={handleSaveReading}
/>
```

## Navigation Components

### Header Navigation
Main site navigation with responsive behavior.

#### Usage
```jsx
// Site Header
<header className="site-header">
  <div className="container">
    <div className="header-content">
      <div className="header-logo">
        <Link to="/" className="logo-link">
          <img src="/logo.svg" alt="TarotLyfe" className="logo" />
        </Link>
      </div>
      
      <nav className="header-nav">
        <ul className="nav-list">
          <li className="nav-item">
            <Link to="/dashboard" className="nav-link">
              Dashboard
            </Link>
          </li>
          <li className="nav-item">
            <Link to="/readings" className="nav-link">
              Readings
            </Link>
          </li>
          <li className="nav-item">
            <Link to="/journal" className="nav-link">
              Journal
            </Link>
          </li>
        </ul>
      </nav>
      
      <div className="header-actions">
        <ThemeToggle />
        <UserMenu />
      </div>
    </div>
  </div>
</header>
```

### Sidebar Navigation
Dashboard sidebar with hierarchical navigation.

#### Usage
```jsx
// Dashboard Sidebar
<aside className="dashboard-sidebar">
  <nav className="sidebar-nav">
    <ul className="nav-list">
      <li className="nav-item">
        <Link to="/dashboard" className="nav-link active">
          <DashboardIcon className="nav-icon" />
          Dashboard
        </Link>
      </li>
      <li className="nav-item">
        <Link to="/draw-card" className="nav-link">
          <CardIcon className="nav-icon" />
          Draw Card
        </Link>
      </li>
      <li className="nav-item">
        <Link to="/journal" className="nav-link">
          <JournalIcon className="nav-icon" />
          Journal
        </Link>
      </li>
    </ul>
  </nav>
</aside>
```

### Breadcrumb Navigation
Hierarchical navigation for deep page structures.

#### Usage
```jsx
// Breadcrumb Navigation
<nav className="breadcrumb">
  <ol className="breadcrumb-list">
    <li className="breadcrumb-item">
      <Link to="/dashboard" className="breadcrumb-link">
        Dashboard
      </Link>
    </li>
    <li className="breadcrumb-separator">/</li>
    <li className="breadcrumb-item">
      <Link to="/journal" className="breadcrumb-link">
        Journal
      </Link>
    </li>
    <li className="breadcrumb-separator">/</li>
    <li className="breadcrumb-item current">
      <span className="breadcrumb-current">New Entry</span>
    </li>
  </ol>
</nav>
```

### Pagination
Navigation for paginated content.

#### Usage
```jsx
// Pagination Component
<nav className="pagination">
  <button className="pagination-btn" disabled>
    <ChevronLeftIcon className="pagination-icon" />
    Previous
  </button>
  
  <div className="pagination-pages">
    <button className="pagination-page active">1</button>
    <button className="pagination-page">2</button>
    <button className="pagination-page">3</button>
    <span className="pagination-ellipsis">...</span>
    <button className="pagination-page">10</button>
  </div>
  
  <button className="pagination-btn">
    Next
    <ChevronRightIcon className="pagination-icon" />
  </button>
</nav>
```

## Accessibility Patterns

### Focus Management
Comprehensive focus management for keyboard navigation.

#### Focus Indicators
```css
/* Global focus styles */
*:focus-visible {
  @apply outline-none ring-2 ring-ring ring-offset-2 ring-offset-background;
}

/* Component-specific focus styles */
.btn:focus-visible {
  @apply ring-2 ring-ring ring-offset-2;
}

.form-input:focus-visible {
  @apply ring-2 ring-ring ring-offset-2;
}

.nav-link:focus-visible {
  @apply ring-2 ring-ring ring-offset-2 rounded-md;
}
```

#### Focus Trapping
```jsx
// Modal Focus Trap
const FocusTrap = ({ children, isActive }) => {
  const trapRef = useRef(null);
  
  useEffect(() => {
    if (isActive && trapRef.current) {
      const focusableElements = trapRef.current.querySelectorAll(
        'button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])'
      );
      
      const firstElement = focusableElements[0];
      const lastElement = focusableElements[focusableElements.length - 1];
      
      firstElement?.focus();
      
      const handleTabKey = (e) => {
        if (e.key === 'Tab') {
          if (e.shiftKey) {
            if (document.activeElement === firstElement) {
              lastElement?.focus();
              e.preventDefault();
            }
          } else {
            if (document.activeElement === lastElement) {
              firstElement?.focus();
              e.preventDefault();
            }
          }
        }
      };
      
      document.addEventListener('keydown', handleTabKey);
      return () => document.removeEventListener('keydown', handleTabKey);
    }
  }, [isActive]);
  
  return <div ref={trapRef}>{children}</div>;
};
```

### ARIA Roles and Labels
Proper ARIA implementation for screen readers.

#### Button ARIA
```jsx
// Button with ARIA
<button 
  className="btn btn-primary"
  aria-label="Draw a new tarot card"
  aria-describedby="draw-card-help"
>
  Draw Card
</button>
<p id="draw-card-help" className="sr-only">
  This will draw a random tarot card for your reading
</p>
```

#### Form ARIA
```jsx
// Form with ARIA
<div className="form-group">
  <label htmlFor="email" className="form-label">
    Email Address
  </label>
  <input 
    type="email"
    id="email"
    className="form-input"
    aria-describedby="email-help email-error"
    aria-invalid={hasError}
    aria-required="true"
  />
  <p id="email-help" className="form-help">
    We'll use this to send you reading reminders
  </p>
  {hasError && (
    <p id="email-error" className="form-error" role="alert">
      Please enter a valid email address
    </p>
  )}
</div>
```

#### Navigation ARIA
```jsx
// Navigation with ARIA
<nav className="header-nav" aria-label="Main navigation">
  <ul className="nav-list" role="menubar">
    <li className="nav-item" role="none">
      <Link 
        to="/dashboard" 
        className="nav-link"
        role="menuitem"
        aria-current={isActive ? "page" : undefined}
      >
        Dashboard
      </Link>
    </li>
  </ul>
</nav>
```

### Keyboard Navigation
Full keyboard support for all interactive elements.

#### Keyboard Shortcuts
```jsx
// Global Keyboard Shortcuts
const useKeyboardShortcuts = () => {
  useEffect(() => {
    const handleKeyDown = (e) => {
      // Cmd/Ctrl + K for search
      if ((e.metaKey || e.ctrlKey) && e.key === 'k') {
        e.preventDefault();
        openSearch();
      }
      
      // Escape to close modals
      if (e.key === 'Escape') {
        closeModal();
      }
      
      // Arrow keys for card navigation
      if (e.key === 'ArrowLeft' || e.key === 'ArrowRight') {
        navigateCards(e.key);
      }
    };
    
    document.addEventListener('keydown', handleKeyDown);
    return () => document.removeEventListener('keydown', handleKeyDown);
  }, []);
};
```

#### Tab Order Management
```jsx
// Dynamic Tab Index Management
const TabOrderManager = ({ children, isActive }) => {
  useEffect(() => {
    const elements = document.querySelectorAll('[tabindex]');
    
    elements.forEach(element => {
      if (isActive) {
        element.removeAttribute('tabindex');
      } else {
        element.setAttribute('tabindex', '-1');
      }
    });
  }, [isActive]);
  
  return children;
};
```

## Animation Guidelines

### Transition Principles
Smooth, purposeful animations that enhance user experience.

#### Duration Guidelines
- **Micro-interactions**: 150-200ms (hover, focus)
- **Component transitions**: 200-300ms (modal open/close)
- **Page transitions**: 300-500ms (route changes)
- **Complex animations**: 500-800ms (card reveals)

#### Easing Functions
```css
/* Standard easing curves */
.ease-standard {
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

.ease-decelerate {
  transition-timing-function: cubic-bezier(0, 0, 0.2, 1);
}

.ease-accelerate {
  transition-timing-function: cubic-bezier(0.4, 0, 1, 1);
}

.ease-bounce {
  transition-timing-function: cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
```

### Hover States
Consistent hover effects across all interactive elements.

#### Button Hover
```css
.btn {
  @apply transition-all duration-200 ease-standard;
}

.btn:hover {
  @apply transform scale-105 shadow-medium;
}

.btn-primary:hover {
  @apply bg-primary/90;
}
```

#### Card Hover
```css
.card-hover {
  @apply transition-all duration-200 ease-standard;
}

.card-hover:hover {
  @apply transform translateY(-2px) shadow-strong;
}
```

### Loading Indicators
Smooth loading states for better perceived performance.

#### Spinner Animation
```css
@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.spinner {
  @apply animate-spin h-4 w-4 border-2 border-current border-t-transparent rounded-full;
}
```

#### Skeleton Loading
```css
@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

.skeleton {
  @apply animate-pulse bg-muted rounded;
}
```

### Card Reveal Animations
Special animations for tarot card interactions.

#### Card Flip Animation
```css
@keyframes cardFlip {
  0% {
    transform: rotateY(0deg);
  }
  50% {
    transform: rotateY(90deg);
  }
  100% {
    transform: rotateY(0deg);
  }
}

.card-flip {
  animation: cardFlip 0.8s ease-in-out;
}
```

#### Card Draw Animation
```css
@keyframes cardDraw {
  0% {
    transform: translateY(100px) scale(0.8);
    opacity: 0;
  }
  50% {
    transform: translateY(-10px) scale(1.05);
    opacity: 0.8;
  }
  100% {
    transform: translateY(0) scale(1);
    opacity: 1;
  }
}

.card-draw {
  animation: cardDraw 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
```

## Component Testing Guidelines

### Accessibility Testing
Automated and manual testing for accessibility compliance.

#### Testing Checklist
- [ ] Keyboard navigation works for all interactive elements
- [ ] Focus indicators are visible and consistent
- [ ] ARIA labels and roles are properly implemented
- [ ] Color contrast meets WCAG 2.1 AA standards
- [ ] Screen reader announcements are appropriate
- [ ] Form validation messages are accessible

#### Testing Tools
```jsx
// Automated accessibility testing
import { axe, toHaveNoViolations } from 'jest-axe';

expect.extend(toHaveNoViolations);

test('Button component should be accessible', async () => {
  const { container } = render(<Button>Click me</Button>);
  const results = await axe(container);
  expect(results).toHaveNoViolations();
});
```

### Visual Regression Testing
Ensure consistent visual appearance across changes.

#### Storybook Integration
```jsx
// Component stories for visual testing
export default {
  title: 'Components/Button',
  component: Button,
  parameters: {
    docs: {
      description: {
        component: 'Primary button component for main actions'
      }
    }
  }
};

export const Primary = {
  args: {
    children: 'Primary Button',
    variant: 'primary'
  }
};

export const AllVariants = () => (
  <div className="space-y-4">
    <Button variant="primary">Primary</Button>
    <Button variant="secondary">Secondary</Button>
    <Button variant="ghost">Ghost</Button>
    <Button variant="danger">Danger</Button>
  </div>
);
```

### Unit Testing
Component behavior and prop handling testing.

#### Testing Examples
```jsx
// Button component tests
describe('Button Component', () => {
  test('renders with correct text', () => {
    render(<Button>Click me</Button>);
    expect(screen.getByRole('button', { name: 'Click me' })).toBeInTheDocument();
  });
  
  test('calls onClick handler when clicked', () => {
    const handleClick = jest.fn();
    render(<Button onClick={handleClick}>Click me</Button>);
    fireEvent.click(screen.getByRole('button'));
    expect(handleClick).toHaveBeenCalledTimes(1);
  });
  
  test('is disabled when disabled prop is true', () => {
    render(<Button disabled>Click me</Button>);
    expect(screen.getByRole('button')).toBeDisabled();
  });
});
```

---

**Document Status**: Complete  
**Last Updated**: 2025-05-30  
**Next Review**: After Phase 1 completion  
**Related Documents**: styleGuide.md, brandContext.md, layoutPatterns.md

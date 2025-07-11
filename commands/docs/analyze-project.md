# /analyze-project

Analyze an existing codebase and generate INITIAL.md template for integrating Context Engineering workflow.

## Execution Flow

1. **Read CLAUDE.md**
   - Access universal development rules from ~/.claude/CLAUDE.md
   - Understand established patterns and conventions
   - Check quality standards and testing requirements

2. **Codebase Analysis**
   - Scan project structure and identify main components
   - Detect programming language, frameworks, and libraries
   - Analyze existing patterns, architecture, and design decisions
   - Identify entry points, main modules, and key functionality

3. **Feature Discovery**
   - Map existing functionality and features
   - Identify models, routes, services, and utilities
   - Understand data flow and component relationships
   - Detect authentication, authorization, and security patterns

4. **Documentation Generation**
   - Create comprehensive INITIAL.md template
   - Document current functionality as baseline
   - Suggest logical next features based on existing code
   - Provide architecture overview and improvement opportunities

## Project Analysis Patterns

### Web Applications
```bash
# Detection patterns:
- app.py, main.py, server.js, index.js
- routes/, controllers/, views/ directories
- templates/, static/ directories
- Database models and migrations

# Analysis focus:
- API endpoints and routes
- Database schema and relationships
- Authentication system
- Frontend/backend separation
- Deployment configuration
```

### APIs (REST/GraphQL)
```bash
# Detection patterns:
- API route definitions
- Model/schema definitions
- Authentication middleware
- Database connections
- Documentation (OpenAPI, GraphQL schema)

# Analysis focus:
- Endpoint inventory
- Data models and relationships
- Authentication/authorization
- Request/response patterns
- Error handling
```

### Libraries/Packages
```bash
# Detection patterns:
- setup.py, package.json, Cargo.toml
- lib/, src/, pkg/ directories
- Public API definitions
- Examples and documentation

# Analysis focus:
- Public interface
- Core functionality
- Dependencies
- Usage patterns
- Extension points
```

## INITIAL.md Template Generation

### Project Overview Section
```markdown
# Existing Project Analysis

## Current State
- **Project Type**: [Detected type and framework]
- **Language**: [Primary language and version]
- **Architecture**: [Monolith/Microservices/etc.]
- **Database**: [Database type and schema overview]
- **Authentication**: [Current auth system]

## Existing Features
[List of current functionality discovered]

## Architecture Overview
[High-level system design and component relationships]
```

### Feature Documentation
```markdown
## Current Functionality

### [Feature Category 1]
- Feature 1: [Description and current implementation]
- Feature 2: [Description and current implementation]

### [Feature Category 2]
- Feature A: [Description and current implementation]
- Feature B: [Description and current implementation]

## API Endpoints (if applicable)
[List of discovered endpoints with methods and purposes]

## Data Models
[Database schema and relationships]

## Dependencies
[Key libraries and frameworks in use]
```

### Next Steps Suggestions
```markdown
## Suggested Next Features
Based on the current codebase, logical next features might include:

1. **[Feature Name]**
   - Why: [Reasoning based on current code]
   - Complexity: [Low/Medium/High]
   - Dependencies: [What needs to exist first]

2. **[Feature Name]**
   - Why: [Reasoning based on current code]
   - Complexity: [Low/Medium/High]
   - Dependencies: [What needs to exist first]

## Technical Debt & Improvements
- [Issues found that violate CLAUDE.md rules]
- [Opportunities for refactoring]
- [Missing tests or documentation]
- [Security or performance concerns]

## Integration Recommendations
- [How to integrate Context Engineering workflow]
- [Suggested first feature to implement with PRP]
- [Areas that need examples/ folder content]
```

## Smart Analysis Features

### Architecture Pattern Recognition
```bash
# Detects common patterns:
- MVC (Model-View-Controller)
- REST API architecture
- Microservices structure
- Layered architecture
- Component-based design
- Database-first vs Code-first
```

### Code Quality Assessment
```bash
# CLAUDE.md rule validation:
- Files exceeding 500 lines
- Missing test coverage
- Undocumented functions
- Code duplication
- Architectural inconsistencies
- Security vulnerabilities
```

### Framework-Specific Analysis
```bash
# Flask/Django projects:
- Route definitions and blueprints
- Model relationships and migrations
- Template structure and static files
- Authentication and session handling

# Express.js/Node.js projects:
- Route handlers and middleware
- Database connections and ORM
- Frontend integration
- Package.json scripts and dependencies

# React/Vue projects:
- Component hierarchy
- State management patterns
- API integration
- Build and deployment setup
```

## Output Examples

### Flask Application Analysis
```
🔍 Analyzing Flask application...

📊 Project Overview:
   • Type: Flask REST API
   • Language: Python 3.9
   • Framework: Flask 2.0 with SQLAlchemy
   • Database: PostgreSQL with migrations
   • Authentication: JWT-based

🏗️ Architecture Analysis:
   • Structure: Modular with blueprints
   • Patterns: Repository pattern, service layer
   • Database: 5 models with proper relationships
   • Testing: 60% coverage with pytest

📋 Discovered Features:
   ✅ User Management
      - User registration and login
      - Profile management
      - JWT authentication
   
   ✅ Product Catalog
      - Product CRUD operations
      - Category management
      - Image upload handling
   
   ✅ Order Processing
      - Shopping cart functionality
      - Order creation and tracking
      - Payment integration (Stripe)

🔍 API Endpoints Found:
   • POST /auth/register - User registration
   • POST /auth/login - User authentication
   • GET /products - List products with pagination
   • POST /products - Create new product (admin)
   • GET /orders - List user orders
   • POST /orders - Create new order

📈 Suggested Next Features:
   1. **Review System** (Medium complexity)
      - Users can review purchased products
      - Rating system with comments
      - Review moderation for admins
   
   2. **Inventory Management** (High complexity)
      - Stock tracking and alerts
      - Supplier management
      - Automated reordering
   
   3. **Email Notifications** (Low complexity)
      - Order confirmations
      - Shipping updates
      - Marketing campaigns

⚠️ Technical Debt Found:
   • 3 files exceed 500 lines (violates CLAUDE.md)
   • Missing tests for payment processing
   • No API documentation
   • Hardcoded configuration values

📝 INITIAL.md Generated: ./INITIAL.md
```

### React Application Analysis
```
🔍 Analyzing React application...

📊 Project Overview:
   • Type: React SPA with TypeScript
   • Framework: React 18 with Next.js
   • State: Redux Toolkit + RTK Query
   • Styling: Tailwind CSS + styled-components
   • Build: Next.js with Vercel deployment

🏗️ Architecture Analysis:
   • Structure: Feature-based organization
   • Patterns: Component composition, custom hooks
   • API: REST integration with axios
   • Testing: 45% coverage with Jest + RTL

📋 Discovered Features:
   ✅ User Dashboard
      - Profile management
      - Settings and preferences
      - Activity history
   
   ✅ Data Visualization
      - Interactive charts (Chart.js)
      - Real-time data updates
      - Export functionality
   
   ✅ Team Collaboration
      - Team member management
      - Role-based permissions
      - Shared workspaces

🎨 UI Components Found:
   • Reusable component library (20+ components)
   • Design system with consistent theming
   • Responsive layout with mobile support
   • Accessibility features implemented

📈 Suggested Next Features:
   1. **Advanced Filtering** (Medium complexity)
      - Multi-criteria search
      - Saved filter presets
      - Advanced sorting options
   
   2. **Real-time Notifications** (Medium complexity)
      - WebSocket integration
      - Push notifications
      - In-app notification center
   
   3. **Offline Support** (High complexity)
      - Service worker implementation
      - Local data caching
      - Sync when online

⚠️ Areas for Improvement:
   • Large bundle size (optimize imports)
   • Missing TypeScript types in some areas
   • Inconsistent error handling
   • No end-to-end testing

📝 INITIAL.md Generated: ./INITIAL.md
```

### Legacy System Analysis
```
🔍 Analyzing legacy codebase...

📊 Project Overview:
   • Type: Monolithic PHP application
   • Framework: Custom framework (legacy)
   • Database: MySQL with no ORM
   • Frontend: jQuery + Bootstrap 3
   • Age: ~8 years old

🏗️ Architecture Analysis:
   • Structure: Traditional MVC pattern
   • Database: 25+ tables with complex relationships
   • Authentication: Session-based with custom security
   • Documentation: Minimal, mostly outdated

📋 Current Functionality:
   ✅ Content Management
      - Article publishing system
      - Media library with file uploads
      - Category and tag management
   
   ✅ User System
      - Multi-role user management
      - Permission-based access control
      - User activity tracking
   
   ✅ E-commerce Module
      - Product catalog management
      - Order processing workflow
      - Payment gateway integration

⚠️ Critical Issues Found:
   • Multiple files exceed 1000+ lines
   • SQL injection vulnerabilities
   • No automated testing
   • Outdated dependencies
   • Mixed business logic in views

📈 Modernization Strategy:
   1. **Security Hardening** (High priority)
      - Fix SQL injection vulnerabilities
      - Update authentication system
      - Implement input validation
   
   2. **Code Refactoring** (High priority)
      - Break down large files
      - Separate concerns properly
      - Add comprehensive testing
   
   3. **API Development** (Medium priority)
      - Create REST API endpoints
      - Enable mobile app development
      - Support third-party integrations

📝 INITIAL.md Generated: ./INITIAL.md
📋 Modernization Roadmap: ./MODERNIZATION.md
```

## Integration with Workflow

### After Analysis
```bash
# Generate project analysis
/analyze-project

# Review generated INITIAL.md
# Edit INITIAL.md to focus on specific next feature

# Start Context Engineering workflow
/branch-strategy feature/first-improvement
/generate-prp INITIAL.md
/execute-prp PRPs/first-improvement.md
```

### Continuous Analysis
```bash
# Re-analyze after major changes
/analyze-project --update
# Updates existing INITIAL.md with new discoveries
```

## Quality Checklist

The command automatically provides:
- [ ] Comprehensive codebase understanding
- [ ] Current feature inventory
- [ ] Architecture and pattern recognition
- [ ] CLAUDE.md compliance assessment
- [ ] Logical next feature suggestions
- [ ] Technical debt identification
- [ ] Integration strategy recommendations
- [ ] Ready-to-use INITIAL.md template

Remember: This analysis provides the foundation for integrating existing projects into your Context Engineering workflow.
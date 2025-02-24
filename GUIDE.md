# Angular Consult Sales Application Documentation

## Project Setup

### Prerequisites
- Node.js and npm installed
- Angular CLI (installed globally)

### Initial Setup

```bash
# Install Angular CLI globally
npm install -g @angular/cli 

# Create new Angular project
ng new angular-consult-sales

# Add NG-ZORRO Ant Design
ng add ng-zorro-antd

# Start the development server on a dynamic port and open in browser
ng serve --port 0 --open 
```

**Important Notes:**
- During NG-ZORRO installation, select "N" for SSR option
- Select LESS as the stylesheet format

## Project Structure

The application follows a modular architecture with the following structure:

### Core Module
Contains singleton services, interceptors, guards, and models that are loaded once in the application.

```bash
# Create core module structure
mkdir -p src/app/core/{services,guards,interceptors,models,exceptions}
ng g module core
```

### Shared Module
Contains reusable components, directives, and pipes that are used across multiple features.

```bash
# Create shared module structure
mkdir -p src/app/shared/{components,directives,pipes,utils}
ng g module shared
```

### Feature Modules
Contains domain-specific functionality, each with its own components, services, and models.

```bash
# Create features directory
mkdir -p src/app/features
```

## Auth Feature

```bash
# Generate authentication module with routing
ng g module features/auth --routing
ng g component features/auth

# Create directory structure
mkdir -p src/app/features/auth/{pages,services,guards,store}
mkdir -p src/app/features/auth/pages/{login,register,forgot-password,reset-password}
mkdir -p src/app/features/auth/store/{actions,reducers,effects,selectors}

# Create auth pages
ng g component features/auth/pages/login
ng g component features/auth/pages/register
ng g component features/auth/pages/forgot-password
ng g component features/auth/pages/reset-password

# Generate guards and services
ng g guard features/auth/guards/auth
ng g service features/auth/services/auth
```

## Users Feature

The Users feature manages user information and operations.

```bash
# Generate users module with routing
ng g module features/users --routing
ng g component features/users

# Create directory structure
mkdir -p src/app/features/users/{pages,shared,models,services,store}
mkdir -p src/app/features/users/pages/{user-dashboard,user-administration}
mkdir -p src/app/features/users/pages/user-administration/components
mkdir -p src/app/features/users/store/{actions,reducers,effects,selectors}

# Create main pages
ng g component features/users/pages/user-dashboard
ng g component features/users/pages/user-administration

# Create specific components for administration
ng g component features/users/pages/user-administration/components/user-create
ng g component features/users/pages/user-administration/components/user-edit
ng g component features/users/pages/user-administration/components/user-detail
ng g component features/users/pages/user-administration/components/user-list

# Create shared module components
ng g component features/users/shared/user-form

# Generate model and service
ng g interface features/users/models/user
ng g service features/users/services/user
```

## Sales Feature

```bash
# Generate sales module with routing
ng g module features/sales --routing
ng g component features/sales

# Create directory structure
mkdir -p src/app/features/sales/{pages,shared,models,services,store}
mkdir -p src/app/features/sales/pages/{sales-dashboard,sales-management}
mkdir -p src/app/features/sales/pages/sales-management/components
mkdir -p src/app/features/sales/store/{actions,reducers,effects,selectors}

# Create main pages
ng g component features/sales/pages/sales-dashboard
ng g component features/sales/pages/sales-management

# Create specific components for sales
ng g component features/sales/pages/sales-management/components/sale-create
ng g component features/sales/pages/sales-management/components/sale-edit
ng g component features/sales/pages/sales-management/components/sale-detail
ng g component features/sales/pages/sales-management/components/sale-list

# Generate model and service
ng g interface features/sales/models/sale
ng g service features/sales/services/sale
```

## Clients Feature

```bash
# Generate clients module with routing
ng g module features/clients --routing
ng g component features/clients

# Create directory structure
mkdir -p src/app/features/clients/{pages,shared,models,services,store}
mkdir -p src/app/features/clients/pages/{client-dashboard,client-management}
mkdir -p src/app/features/clients/store/{actions,reducers,effects,selectors}

# Create components
ng g component features/clients/pages/client-dashboard
ng g component features/clients/pages/client-management
ng g component features/clients/pages/client-management/components/client-create
ng g component features/clients/pages/client-management/components/client-edit
ng g component features/clients/pages/client-management/components/client-detail
ng g component features/clients/pages/client-management/components/client-list

# Generate model and service
ng g interface features/clients/models/client
ng g service features/clients/services/client
```

## Dashboard/Analytics Feature

```bash
# Generate dashboard module with routing
ng g module features/dashboard --routing
ng g component features/dashboard

# Create charts and widgets components
mkdir -p src/app/features/dashboard/components/{charts,widgets}
ng g component features/dashboard/components/charts/sales-chart
ng g component features/dashboard/components/charts/clients-chart
ng g component features/dashboard/components/widgets/summary-card
ng g component features/dashboard/components/widgets/performance-indicator
```

## Shared Components

```bash
# Generate loading and alert components
ng g component shared/components/loading
ng g component shared/components/alert
```

## HTTP Interceptors

```bash
# Generate HTTP interceptors for auth and error handling
ng g interceptor core/interceptors/auth
ng g interceptor core/interceptors/error
```

## Core Services

```bash
# Generate HTTP services
ng g service core/services/http
```

## Environmental Configuration

```bash
# Ensure environment files are properly set up
mkdir -p src/environments
touch src/environments/environment.ts
touch src/environments/environment.prod.ts
```

## State Management

The application uses the NgRx library for state management with a store, actions, reducers, effects, and selectors for each feature module.

```bash
# Install NgRx packages
npm install @ngrx/store @ngrx/effects @ngrx/entity @ngrx/store-devtools

# Install additional utility libraries
npm install moment lodash chart.js ng2-charts
```

## Global Styling

```bash
# Create global styles directory
mkdir -p src/assets/styles
touch src/assets/styles/variables.less
touch src/assets/styles/mixins.less
touch src/assets/styles/global.less
```

## Localization Support

```bash
# Add i18n support
mkdir -p src/assets/i18n
touch src/assets/i18n/en.json
touch src/assets/i18n/es.json
```

## Testing Setup

```bash
# Create test helpers
mkdir -p src/testing
touch src/testing/test-helpers.ts
```

## Documentation

```bash
# Set up documentation structure
mkdir -p docs/{architecture,development,endpoints,deployment}
touch docs/architecture/ACHITECTURE_GUIDE.md
touch docs/development/DEVELOPMENT_GUIDE.md
touch docs/endpoints/ENDPOINTS_GUIDE.md
touch docs/deployment/DEPLOYMENT_GUIDE.md
```

## Next Steps

1. Configure core module to provide services
2. Set up shared module to export components
3. Implement routing for feature modules
4. Create models for data structures
5. Implement services for API communication
6. Configure NgRx store for state management
7. Implement authentication flow
8. Set up HTTP interceptors for request/response handling
9. Design and implement dashboard analytics
10. Configure internationalization support

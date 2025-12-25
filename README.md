# Predictive Maintenance System - React Frontend

## Overview

This is the **React + TypeScript** frontend for the Predictive Maintenance System, built to consume the C# .NET Web API backend. It provides a modern, responsive user interface for managing industrial machine health monitoring and maintenance scheduling.

## Technology Stack

- **Framework**: React 19.x with TypeScript
- **Build Tool**: Create React App
- **Styling**: Tailwind CSS
- **HTTP Client**: Axios
- **Routing**: React Router v6
- **Forms**: React Hook Form
- **Notifications**: React Hot Toast
- **Icons**: Heroicons
- **State Management**: React Hooks (useState, useEffect)

## Features

✅ **Dashboard**: Real-time statistics and system overview  
✅ **Machine Management**: Add, edit, delete, and search machines  
✅ **Health Monitoring**: Visual health scores and status indicators  
✅ **Alert Management**: View and manage system alerts  
✅ **Maintenance Scheduling**: Track upcoming and overdue maintenance  
✅ **Reports**: Generate system reports and analytics  
✅ **Responsive Design**: Mobile-friendly interface  
✅ **Real-time Updates**: Auto-refreshing data  
✅ **Form Validation**: Client-side validation with error handling  
✅ **API Integration**: Full integration with C# .NET backend  

## Project Structure

```
frontend/
├── public/                     # Static assets
│   ├── index.html             # HTML template
│   └── favicon.ico            # App icon
├── src/
│   ├── components/            # Reusable components
│   │   └── Layout.tsx         # Main layout with navigation
│   ├── pages/                 # Page components
│   │   ├── Dashboard.tsx      # Main dashboard
│   │   ├── MachinesPage.tsx   # Machine management
│   │   ├── AlertsPage.tsx     # Alert management
│   │   ├── MaintenancePage.tsx# Maintenance scheduling
│   │   └── ReportsPage.tsx    # Reports and analytics
│   ├── services/              # API services
│   │   └── api.ts             # HTTP client and API calls
│   ├── types/                 # TypeScript interfaces
│   │   └── index.ts           # All type definitions
│   ├── App.tsx                # Main app component
│   ├── App.css                # Global styles
│   └── main.tsx               # App entry point
├── package.json               # Dependencies and scripts
├── tailwind.config.js         # Tailwind CSS configuration
├── tsconfig.json              # TypeScript configuration
└── vite.config.ts             # Vite configuration (if using Vite)
```

## Prerequisites

1. **Node.js** (v16 or higher)
   ```bash
   # macOS with Homebrew
   brew install node
   ```

2. **C# .NET Backend** running on port 8080
   ```bash
   # Start the backend first
   ./run-csharp-mac.sh
   ```

## Installation & Setup

### Option 1: Use the Startup Script (Recommended)
```bash
# From project root directory
./run-react-frontend.sh
```

### Option 2: Manual Setup
```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install --legacy-peer-deps

# Start development server
npm start
```

The frontend will be available at: http://localhost:3000

## Available Scripts

- `npm start` - Start development server
- `npm build` - Build for production
- `npm test` - Run tests
- `npm run eject` - Eject from Create React App (irreversible)

## API Integration

The frontend communicates with the C# .NET backend via REST API calls:

### Base URL
```
http://localhost:8080/api
```

### Key Endpoints Used
- `GET /machines` - All machines
- `POST /machines` - Create machine
- `GET /machines/statistics` - Dashboard stats
- `GET /machines/attention` - Critical machines
- `GET /machines/active-alerts` - Active alerts
- `GET /machines/upcoming-maintenance` - Scheduled maintenance

### API Service
The `src/services/api.ts` file provides:
- HTTP client configuration with Axios
- Request/response interceptors
- Typed API methods for all endpoints
- Error handling and logging

## Component Architecture

### Layout Component
- Header with branding and version info
- Navigation menu with active state
- Footer with API documentation links
- Responsive design for mobile/desktop

### Dashboard
- Statistics cards with real-time data
- Critical machines overview
- Active alerts summary
- Upcoming maintenance preview
- Quick action buttons

### MachinesPage
- Searchable and filterable machine table
- Add new machine modal form
- Health score visualization
- Status indicators
- CRUD operations

### AlertsPage
- Alert listing with severity indicators
- Filtering by severity and status
- Acknowledge/resolve actions
- Time-based sorting

### MaintenancePage
- Upcoming maintenance schedule
- Priority and status indicators
- Technician assignments
- Duration estimates

### ReportsPage
- System overview statistics
- Exportable reports
- Health distribution charts
- Performance analytics

## Styling & Design

### Design System
- **Colors**: Industrial theme with blue primary, status colors
- **Typography**: Inter font family for readability
- **Icons**: Heroicons for consistent iconography
- **Layout**: CSS Grid and Flexbox for responsive design

### Tailwind CSS Classes
- Custom component classes in `App.css`
- Responsive utilities
- Animation classes
- Form styling
- Table formatting

### Status Color Coding
- **Green**: Active, healthy, completed
- **Yellow**: Warning, maintenance, scheduled
- **Red**: Critical, emergency, overdue
- **Blue**: Info, in-progress, default
- **Gray**: Inactive, decommissioned

## Development Guidelines

### Adding New Features
1. **Types**: Add interfaces to `src/types/index.ts`
2. **API**: Add service methods to `src/services/api.ts`
3. **Components**: Create in appropriate folder
4. **Routing**: Add routes to `src/App.tsx`
5. **Styling**: Use Tailwind classes, custom CSS in `App.css`

### Best Practices
- Use TypeScript for type safety
- Implement proper error handling
- Add loading states for async operations
- Use React Hook Form for forms
- Show user feedback with toast notifications
- Follow responsive design principles

## Testing

```bash
# Run tests
cd frontend
npm test

# Run with coverage
npm test -- --coverage

# Build for production
npm run build
```

## Production Deployment

### Build Process
```bash
cd frontend
npm run build
```

This creates a `build/` folder with optimized production files.

### Environment Variables
Create `.env` files for different environments:

**.env.development**
```
REACT_APP_API_URL=http://localhost:8080/api
REACT_APP_VERSION=1.0.0
```

**.env.production**
```
REACT_APP_API_URL=https://your-production-api.com/api
REACT_APP_VERSION=1.0.0
```

## Backend Integration

The React frontend is designed to work with the C# .NET backend:

### Data Flow
1. React components make API calls via `services/api.ts`
2. API calls go to C# .NET controllers
3. Controllers use services and repositories
4. Entity Framework manages database operations
5. Data flows back through the same chain

### Type Safety
- TypeScript interfaces match C# entity models
- API responses are strongly typed
- Form validation matches backend requirements

## Troubleshooting

### Common Issues

**CORS Errors**: Ensure C# backend has CORS enabled for `http://localhost:3000`

**API Connection Failed**: 
- Check if C# backend is running on port 8080
- Verify API endpoints in browser: http://localhost:8080/swagger

**Build Errors**:
- Delete `node_modules/` and run `npm install --legacy-peer-deps`
- Check TypeScript errors in console

**Styling Issues**:
- Ensure Tailwind CSS is properly installed
- Check if CSS is being processed correctly

### Debug Mode
Add to `.env.development`:
```
REACT_APP_DEBUG=true
```

This enables additional console logging for API calls and state changes.

## Contributing

1. Follow TypeScript strict mode guidelines
2. Use Prettier for code formatting
3. Add proper error handling for all async operations
4. Include loading states for user experience
5. Write meaningful commit messages
6. Test across different screen sizes

## Support

For issues with the React frontend:
- Check browser console for JavaScript errors
- Verify API connectivity with network tab
- Ensure all dependencies are installed
- Check that backend is running and accessible

The React frontend provides a modern, intuitive interface for the Predictive Maintenance System while maintaining full integration with the C# .NET backend.

# Project Management and Development Guidelines

## Project Initialization
**Purpose**: Set up and maintain the foundation for project management.

## Task Execution
**Purpose**: Break down user requests into actionable steps.

### Guidelines:
1. Split tasks into **clear, numbered steps** with explanations for actions and reasoning
2. Identify and flag potential issues before they arise
3. Verify completion of each step before proceeding
4. If errors occur:
   - Document them
   - Revert to previous steps
   - Retry as needed

## Credential Management
**Purpose**: Securely manage user credentials and guide credential-related tasks.

### Guidelines:
1. Clearly explain the purpose of credentials requested from users
2. Guide users in obtaining any missing credentials
3. Validate credentials before proceeding with any operations
4. Avoid storing credentials in plaintext; provide guidance on secure storage
5. Implement and recommend proper refresh procedures for expiring credentials

## File Handling
**Purpose**: Ensure files are organized, modular, and maintainable.

### Guidelines:
1. Keep files modular by breaking large components into smaller sections
2. Store constants, configurations, and reusable strings in separate files
3. Use descriptive names for files and folders for clarity
4. Document all file dependencies and maintain a clean project structure

## Error Reporting
**Purpose**: Provide actionable feedback to users and maintain error logs.

### Guidelines:
1. Create detailed error reports, including context and timestamps
2. Suggest recovery steps or alternative solutions for users
3. Track error history to identify patterns and improve future responses
4. Escalate unresolved issues with context to appropriate channels

## Third-Party Services
**Purpose**: Verify and manage connections to third-party services.

### Guidelines:
1. Ensure all user setup requirements, permissions, and settings are complete
2. Test third-party service connections before using them in workflows
3. Document version requirements, service dependencies, and expected behavior
4. Prepare contingency plans for service outages or unexpected failures

## Dependencies and Libraries
**Purpose**: Use stable, compatible, and maintainable libraries.

### Guidelines:
1. Always use the most stable versions of dependencies to ensure compatibility
2. Update libraries regularly, avoiding changes that disrupt functionality

## Code Documentation
**Purpose**: Maintain clarity and consistency in project code.

### Guidelines:
1. Write clear, concise comments for all sections of code
2. Use **one set of triple quotes** for docstrings to prevent syntax errors
3. Document the purpose and expected behavior of functions and modules

## Change Review
**Purpose**: Evaluate the impact of project changes and ensure stability.

### Guidelines:
1. Review all changes to assess their effect on other parts of the project
2. Test changes thoroughly to ensure consistency and prevent conflicts
3. Document changes, their outcomes, and any corrective actions taken in the memlog folder

## Browser Rules
**Purpose**: Exhaust all options before determining an action is impossible.

### Guidelines:
1. When evaluating feasibility, check alternatives in all directions: **up/down** and **left/right**
2. Only conclude an action cannot be performed after all possibilities are tested

## Component Structure Update (2024-03-20)

### File Upload System Components

1. High-Level Components:
   - `FileUpload.tsx` (Primary component)
     - Handles file upload, validation, compression
     - Uses DropZone for drag-and-drop
     - Manages file list and preview
     - Provides comprehensive file handling solution

2. Supporting Components:
   - `DropZone.tsx` (Low-level component)
     - Pure drag-and-drop functionality
     - Used by FileUpload
     - Can be used independently for simple drag-drop needs

3. Preview Components (in FilePreview directory):
   - `FilePreview/index.tsx` - Main preview component
   - `FilePreview/FilePreviewUtils.ts` - Utility functions
   - `FilePreview/FilePreviewTypes.ts` - Type definitions

4. Utility Files:
   - `utils/fileUtils.ts` - File handling utilities
     - Validation functions
     - Compression utilities
     - Type definitions

### Deprecated Components
The following components are now deprecated and should be removed:
- `DocumentUpload.tsx` (replaced by FileUpload)
- `FilePreview.tsx` (moved to FilePreview directory)
- `ImageCompressor.tsx` (functionality moved to fileUtils)

### Component Usage Guidelines
1. For full file upload functionality:
   ```tsx
   import { FileUpload } from '../components/common/FileUpload';
   ```

2. For simple drag-and-drop:
   ```tsx
   import { DropZone } from '../components/common/DropZone';
   ```

3. For file preview only:
   ```tsx
   import { FilePreview } from '../components/common/FilePreview';
   ```

### Next Steps
1. Remove deprecated components
2. Update all imports to use new component structure
3. Add migration guide for existing code
4. Update tests to reflect new structure

## Digital Vehicle Assessment App - Component Structure and Updates

## Recent Updates (2024-02-24)

### New Features and Improvements

1. **Image Preview System**
   - Full-screen preview capability
   - Zoom overlay on hover
   - Responsive preview dialog
   - Consistent thumbnail sizing

2. **App State Management**
   - Global state management via AppStateContext
   - Reset functionality with two options:
     - Full app reset (returns to login)
     - Assessment reset (returns to welcome)
   - Floating reset button with confirmations

3. **Loading State Improvements**
   - Enhanced loading context
   - Form submission loading messages
   - Fixed loading state management
   - Better error handling

4. **Photo Guide Enhancements**
   - Photo confirmation step
   - Improved preview functionality
   - Retake photo capability
   - Skip option for optional photos

## Component Structure

### High-level Components

1. **Forms**
   - `UserDetailsForm`: Collects user information
   - `IncidentDetailsForm`: Manages incident information
   - `PhotoGuide`: Handles vehicle photo collection
   - `DocumentUploadForm`: Manages document uploads

2. **Common Components**
   - `FileUpload`: Handles file uploads with drag-and-drop
   - `FilePreview`: Shows file previews with zoom
   - `ImagePreview`: Full-screen image viewing
   - `LoadingOverlay`: Loading state display
   - `ResetButton`: App state management

3. **Context Providers**
   - `AppStateProvider`: Global app state
   - `LoadingProvider`: Loading states
   - `ToastProvider`: Notifications
   - `ConfirmationProvider`: Confirmation dialogs

### Supporting Components

1. **Preview Components**
   - Image preview with zoom
   - Document preview
   - Photo gallery view

2. **Utility Files**
   - File validation
   - Image compression
   - Type definitions
   - Form helpers

3. **Layout Components**
   - Navigation
   - Form layouts
   - Responsive containers

## Next Development Priorities

### Immediate Focus (Next Sprint)
1. **Data Persistence**
   - Implement local storage strategy
   - Add form auto-save
   - Handle offline data

2. **User Experience**
   - Add progress tracking
   - Implement breadcrumbs
   - Enhance form navigation

3. **Photo Management**
   - Add categorization
   - Implement annotation
   - Add batch uploads

### Short-term Goals
1. **Authentication**
   - User authentication
   - Role-based access
   - Session management

2. **Reporting**
   - Assessment summaries
   - PDF export
   - Data visualization

3. **Testing**
   - Unit tests
   - Integration tests
   - E2E testing

### Long-term Vision
1. **Platform Evolution**
   - AI damage detection
   - Real-time collaboration
   - Mobile app development

## Usage Guidelines

### File Upload
1. Use `FileUpload` for all file inputs
2. Configure accepted file types
3. Set appropriate size limits

### Photo Guide
1. Follow the step sequence
2. Use confirmation dialogs
3. Allow photo retakes

### Form Submission
1. Handle loading states
2. Show clear feedback
3. Validate all inputs

## Best Practices

1. **State Management**
   - Use context for global state
   - Keep form state local
   - Handle loading properly

2. **Error Handling**
   - Show clear messages
   - Log errors appropriately
   - Provide recovery options

3. **Performance**
   - Optimize image loading
   - Use lazy loading
   - Implement caching

## Known Issues & Solutions

1. **Loading States**
   - Use LoadingContext consistently
   - Show meaningful messages
   - Handle errors gracefully

2. **Image Preview**
   - Optimize large files
   - Cache previews
   - Handle memory properly

3. **Form Validation**
   - Consistent feedback
   - Clear error messages
   - Proper field validation

## Project Requirements

### Digital Vehicle Assessment App Overview
A web-based application for digital vehicle assessment with the following features:

1. **Authentication**
   - Reference number-based login
   - Welcome page with assessment guide

2. **Multi-Step Assessment Process**
   - Personal details confirmation
   - Vehicle information
   - Incident details
   - Document upload (optional)
   - Digital photo guide

3. **Photo Guide Requirements**
   - Vehicle exterior:
     - Registration
     - Front view
     - Right front
     - Right side
     - Right rear
     - Rear view
     - Left rear
     - Left side
     - Left front
   - Wheels and tires:
     - Right front rim
     - Right front tire
     - (Repeat for all wheels)
     - Spare wheel
   - Additional components:
     - Jack and tools
     - Engine bay
   - Interior:
     - Front interior
     - Transmission type (auto/manual)
     - Mileage photo
     - Rear interior
   - Incident documentation:
     - Close-up damage photos
     - Wide-angle context photos

### Technical Stack
- Frontend: React with MUI
- Backend: Supabase
- Additional Features:
  - Frontend image compression
  - Drag-and-drop functionality
  - Mobile-responsive design
  - Guided photo capture interface

## Digital Vehicle Assessment App - Development Instructions

## Recent Updates (2024-02-24)

### Progress Tracking System Implementation

1. **New Components & Context**
   - Added `ProgressContext` for centralized progress management
   - Created `ProgressStepper` component for visual progress tracking
   - Implemented `ReviewStep` component for final assessment review

2. **Form Data Persistence**
   - Added localStorage-based persistence for form data
   - Automatic saving of progress and form data
   - Data recovery on page reload

3. **Navigation Improvements**
   - Step validation before navigation
   - Warning dialogs for incomplete steps
   - Proper routing with assessment sub-routes

### Important Development Guidelines

1. **Functionality Preservation**
   - NEVER remove existing functionality unless explicitly requested
   - Always maintain backward compatibility
   - Document any changes that affect existing features

2. **Context Provider Hierarchy**
   ```
   ThemeProvider
   └── ToastProvider
       └── LoadingProvider
           └── ConfirmationProvider
               └── Router
                   └── AppStateProvider
                       └── ProgressProvider
                           └── AppContent
   ```

3. **Form Component Structure**
   - Each form should use the progress tracking system
   - Implement `markStepComplete` on successful submission
   - Include proper validation and error handling
   - Maintain data persistence

4. **Progress Tracking Integration**
   - Forms should call `markStepComplete` after successful submission
   - Use `canNavigateToStep` for navigation validation
   - Implement proper error handling and user feedback

### Component Dependencies

1. **Required Providers**
   - ToastProvider (for notifications)
   - LoadingProvider (for loading states)
   - ConfirmationProvider (for dialogs)
   - ProgressProvider (for progress tracking)
   - AppStateProvider (for global state)

2. **Form Components**
   - Must implement progress tracking
   - Should handle data persistence
   - Need proper validation
   - Should provide user feedback

### Next Development Priorities

1. **Data Management**
   - Implement comprehensive form data validation
   - Add auto-save functionality
   - Implement data export features

2. **User Experience**
   - Add form field validation feedback
   - Improve navigation between steps
   - Enhance mobile responsiveness

3. **Testing**
   - Add unit tests for new components
   - Implement integration tests
   - Add end-to-end testing

### Known Issues & Considerations

1. **Progress Tracking**
   - Ensure proper step validation
   - Handle edge cases in navigation
   - Maintain progress state consistency

2. **Form Data**
   - Handle large form data sets
   - Implement proper data cleanup
   - Consider offline support

3. **Performance**
   - Monitor localStorage usage
   - Optimize form rendering
   - Handle large file uploads efficiently

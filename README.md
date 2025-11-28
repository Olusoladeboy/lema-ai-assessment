# Web Developer Assignment

This full-stack assignment involves building a user management system where developers must extend a Node.js/SQLite backend for user and post operations, and create a React/TypeScript frontend that displays user data in a paginated table and allows for post management, all while following provided design specifications.

## Live URLs

- **Frontend**: [https://lema-ai-frontend.vercel.app/](https://lema-ai-frontend.vercel.app/)
- **Backend**: [https://lema-ai-backend-production.up.railway.app/](https://lema-ai-backend-production.up.railway.app/)

## Setup Instructions for Local Installation

### Prerequisites

- Node.js (v18 or higher recommended)
- npm or yarn

### How to Run the Backend

1. Navigate to the backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Build the TypeScript code:
```bash
npm run build
```

4. Start the backend server:
```bash
npm start
```

For development with auto-reload:
```bash
npm run dev
```

The backend server will run on `http://localhost:3001`.

**Note**: The backend uses an SQLite database (`data.db`) that is already included in the project. No additional database setup is required.

### How to Run the Frontend

1. Navigate to the frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file (if not already present) with the backend URL:
```bash
echo "VITE_API_BASE_URL=http://localhost:3001" > .env
```

4. Start the development server:
```bash
npm run dev
```

The frontend application will be available at `http://localhost:5173` (or the next available port).

### How to Run Tests

#### Backend Tests
```bash
cd backend
npm test
```

#### Frontend Tests
```bash
cd frontend
npm test
```

For frontend tests with UI:
```bash
cd frontend
npm run test:ui
```

## Backend

### Provided Backend

A Node server written in TypeScript is provided.
The server utilizes an SQLite database (data.db) containing all relevant data, including users posts and addresses.
The server exposes several partial RESTful API endpoints:

User Endpoints:
- `GET /users` -  Returns a list of users with pagination support. (e.g., /users?pageNumber=0&pageSize=10).
- `GET /users/count` - Returns the total number of users.
Post Endpoint:
- `GET /posts` - Returns posts filtered by a specific user ID, using the userId query parameter (e.g., /posts?userId={userId}).

### Backend Requirements

You are required to implement the following backend functionalities:

- **Address to User**
  - Extend the existing user-related endpoints to include address (metadata associated with the user).
  - Query the address from the database and include them in the user response.
  - Ensure the address are properly validated and formatted before returning to the frontend.
- **Post Deletion**
  - Create an endpoint to delete a post by its ID.
  - Remove the post from the database upon successful deletion.
  - Return appropriate HTTP status codes and messages.
- **Add a New Post**
  - Create an endpoint to add a new post for a user, accepting **Title**, **Body**, and **User ID**.
  - Validate input data and handle errors.
  - Save the new post to the database upon success.

## Front-End

### General Requirements

- Implement the web UI using **TypeScript**, **React**, **React Query**, and **Tailwind CSS**.
- Follow the **Tailwind** and **shadcn/ui** design tokens (defined in Figma) for consistent styling.
- Follow the **Figma design** provided in the Resources section.
- Ensure **graceful handling of API errors** or unexpected data from the backend.
- Components and pages should have **error and loading states**.
- Emphasize **code reusability** and **separation of concerns** in your components.

### Users Table

- Set up an internal API that fetches a list of users from your backend API, using the pagination.
- Display the users in an organized table with the following features:
  - **Pagination**: Show 4 users per page.
  - **User Details**:
    - Full Name
    - Email Address
    - Address formatted as "street, state, city, zipcode". Keep the address column at 392px width and use ellipsis (...) for any overflow.

### User Posts

- When clicking on a user row, navigate to a new page that displays a list of the user's posts.
- Fetch the user's posts from your backend API.
- The page should include:
  - A header with a summary of the user and the number of posts.
  - A list of all posts (**no pagination required**).
  - Each post should display:
    - **Title**
    - **Body**
    - A **Delete** icon.
      - Clicking the Delete icon should delete the post via your backend API and update the UI accordingly.
  - An option to **add a new post**:
    - Include a button that opens a form to create a new post with **Title** and **Body** fields.
    - Upon submission, the new post should be saved via your backend API and appear in the list of posts without requiring a page refresh.
- Ensure the design is intuitive and posts are easily readable by closely following the provided Figma design.

## Guidelines

1. **State Management with React Query**
   - Use React Query to manage server state.
   - Ensure efficient data fetching, caching, and synchronization with the backend.
   - Utilize React Query's features to handle loading and error states.
2. **Code Reusability and Separation**
   - Structure your components to promote reusability and maintainability.
   - Abstract shared logic into custom hooks or utility functions where appropriate.
   - Follow best practices for component composition and props management.
3. **Responsiveness**
   - Ensure the application is responsive and functions well on various screen sizes and devices.
   - Use Tailwind CSS utilities to create responsive layouts.
4. **Error Handling**
   - Implement robust error handling for API requests and unexpected data.
   - Provide meaningful feedback to the user in case of errors.
   - Use try-catch blocks and handle promise rejections appropriately in your backend.

## Resources

- **Backend Server**: A partially implemented Node server in TypeScript will be provided. You are expected to complete the specified backend functionalities.
- **SQLite Database**: The backend uses the `data.db` SQLite database, which contains all necessary data.
- **Figma Design**: Follow the design specifications outlined in the provided Figma file.
  [Figma Design for Web UI](https://www.figma.com/design/Wkbz27sGWBOFMDocOck4mm/Full-Stack-Developer-Assignment?node-id=0-1&node-type=canvas&t=zK4X8qKaPmxu84XZ-0)

## Deliverables

- A full-stack application that meets the above requirements.
- Source code organized and documented for readability.
- Completed backend functionalities as specified.
- At least one unit test demonstrating testing of a component or functionality.
- Instructions on how to run the application locally, including setting up the backend and frontend.

## Setup Instructions

### Prerequisites

- Node.js (v18 or higher recommended)
- npm or yarn

### Backend Setup

1. Navigate to the backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Build the TypeScript code:
```bash
npm run build
```

4. Start the backend server:
```bash
npm start
```

The backend server will run on `http://localhost:3001`.

**Note**: The backend uses an SQLite database (`data.db`) that is already included in the project. No additional database setup is required.

### Frontend Setup

1. Navigate to the frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

The frontend application will be available at `http://localhost:5173` (or the next available port).

### Running Tests

#### Backend Tests
```bash
cd backend
npm test
```

#### Frontend Tests
```bash
cd frontend
npm test
```

## Project Structure

```
.
├── backend/          # Node.js/TypeScript backend
│   ├── src/         # Source TypeScript files
│   ├── dist/        # Compiled JavaScript files
│   ├── data.db      # SQLite database
│   └── package.json
├── frontend/        # React/TypeScript frontend
│   ├── src/         # Source files
│   │   ├── api/     # API client
│   │   ├── components/  # React components
│   │   ├── hooks/   # Custom hooks
│   │   ├── pages/   # Page components
│   │   └── types/   # TypeScript types
│   └── package.json
└── README.md
```

## API Endpoints

### Users
- `GET /users?pageNumber={page}&pageSize={size}` - Get paginated users
- `GET /users/count` - Get total user count

### Posts
- `GET /posts?userId={userId}` - Get posts for a user
- `POST /posts` - Create a new post (requires: `title`, `body`, `userId`)
- `DELETE /posts/{postId}` - Delete a post

## Features Implemented

### Backend
- ✅ Address formatting and inclusion in user responses
- ✅ Post deletion endpoint
- ✅ Create new post endpoint with validation
- ✅ Error handling and appropriate HTTP status codes

### Frontend
- ✅ Users table with pagination (4 users per page)
- ✅ User details display (name, email, formatted address)
- ✅ Address column with fixed width (392px) and text truncation
- ✅ User posts page with user information
- ✅ Post list display
- ✅ Create new post functionality
- ✅ Delete post with optimistic updates
- ✅ Loading and error states
- ✅ React Query for data fetching and caching
- ✅ Responsive design with Tailwind CSS
- ✅ Unit tests for API functions and components

## Testing

The project includes unit tests for both backend and frontend:

- **Backend**: Tests for post deletion endpoint
- **Frontend**: Tests for API functions and React components

Run tests with:
```bash
# Backend
cd backend && npm test

# Frontend
cd frontend && npm test
```

## Submission Instructions

- **Code Repository**: Provide access to your code via a Git repository (e.g., GitHub, GitLab).
- **Readme File**: This README includes instructions on how to install dependencies, set up the database, and start both the backend and frontend servers.

# React Router Dom v6 - Unexpected Crash with Undefined Dynamic Route Segment

This repository demonstrates a bug in React Router Dom v6 where navigating to a route with a dynamic segment that's not defined causes the application to crash without a helpful error message.  The issue is particularly subtle and can be hard to debug.

## Bug Description

The application uses `react-router-dom` v6. When the user tries to navigate to a route expecting a dynamic segment (e.g., `/users/:id`), and the `:id` part isn't provided or is invalid, the application crashes silently, without providing a clear error message in the console.

## Steps to Reproduce

1. Clone this repository.
2. Run `npm install`.
3. Run `npm start`.
4. Navigate to `/users/123` (this works).
5. Now navigate to `/users/` or `/users`.  The application will crash silently.

## Solution

The solution involves using `useParams` hook in a more robust manner, making sure to handle cases where the dynamic segment is missing, null, undefined or empty.  Also, adding error boundaries is a good practice for handling unexpected errors in React.
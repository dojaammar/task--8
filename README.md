Task Management Platform
Table of Contents
2. Project Structure (folders & files)
3. Database Models (Mongoose schemas)
4. API Endpoints
5. Middleware
6. Authentication
7. Error Handling
8. Technical Research Topics
9. Notes for Students / Acceptance Criteria

---
## 2. Project Structure

```
├── node_modules
├── src
│   ├── controllers/
│   │   ├── auth.controller.js
│   │   ├── project.controller.js
│   │   ├── task.controller.js
│   │   ├── analytics.controller.js
│   │   └── notification.controller.js
│   ├── middleware
│   │   ├── auth.middleware.js             
│   │   └── error.middleware.js            
│   ├── models
│   │   ├── User.js
│   │   ├── Project.js
│   │   ├── Task.js
│   │   └── Notification.js
│   ├── routes
│   │   ├── auth.routes.js
│   │   ├── project.routes.js
│   │   ├── task.routes.js
│   │   └── notification.routes.js
│   ├── utils                
│   │   ├── tokenService.js            
│   │   └── notificationService.js      
│   ├── app.js                     
├── .env
├── .gitIgnore
├── package-lock.json
├── package.json
└── README.md
```

## 3. Database Models

* User:
  name(String, Required),
  email(String, Required, Unique),
  password(String, Required (Stored as a hashed value)),
settings.
* Project:
 name(String, Required.),
  description,
 owner(ObjectId (Reference: User).),
  members([ObjectId] (Reference: User), the list of team members.)
* Task:
 title(String, Required.),
   description,
   project(ObjectId (Reference: Project), optional for personal tasks.),
   creator(ObjectId (Reference: User), Required),
    assignees(ObjectId (Reference: User), Required),
  status(String ('todo', 'in progress', 'done').),
   priority(String (e.g., 'low', 'high'), Required.),
   dueDate(Date.)
* Notification: recipient: ObjectId (Reference: User), Required.
            -sourceUser: ObjectId (Reference: User), who initiated the action.
            -type: String ('assignment', 'deadline').
            -targetResource: ObjectId (Reference: Task/Project), the ID of the related item.
            -deliveryType: [String] ( ['web', 'email'] ), the channels to use.
            -isRead: Boolean, read status.
## 4. API Endpoints

* Auth: register, login
* Users: get current user
* Projects: create, list, get by ID, invite members
* Tasks: create, list, get by ID, update, delete, add reminder
* Invitations: accept
* Notifications: list, mark read
* Analytics: overview

## 5. Middleware

* auth: verify JWT
* permission: check project ownership/membership
* validate: request validation
* errorHandler: centralized error handling

## 6. Authentication

* JWT access tokens for protected routes
* Optional refresh tokens
* Hash passwords with bcrypt
* Use HTTPS in production

## 7. Error Handling

* Centralized middleware with standard error classes: BadRequest, NotFound, Unauthorized, Forbidden, Conflict
* Log errors and provide generic messages to users

## 8. Technical Research Topics

* JWT authentication and refresh flow
* MongoDB relationships and schema design
* Express.js middleware and routing
* Mongoose transactions
* RESTful API best practices
* Password security with bcrypt
* Job scheduling in Node.js
* Real-time notifications

## 9. Notes for Students / Acceptance Criteria

* Unit and integration tests for endpoints
* Input validation and sanitization
* Secure password storage and JWT usage
* Clear MVP definition and feature flow
* Document business rules and edge cases



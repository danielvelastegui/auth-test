# NestJS Auth0 Authentication

This is a sample project demonstrating how to implement authentication using Auth0 in a NestJS application. Auth0 is a powerful authentication and identity management platform that allows you to add secure authentication to your applications with ease.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
    - [Configuration](#configuration)
    - [Run the Application](#run-the-application)
- [Usage](#usage)
    - [Protected Routes](#protected-routes)
- [Contributing](#contributing)
- [License](#license)

## Introduction

NestJS is a progressive Node.js framework for building efficient, scalable, and maintainable server-side applications. Auth0 is a widely-used authentication service that provides user authentication, identity management, and access control for your applications.

This project serves as a starting point for integrating Auth0 authentication into your NestJS application, allowing you to secure your APIs and protect your routes.

## Features

- JWT-based authentication with Auth0.
- Authentication guards to protect routes and endpoints.

## Prerequisites

Before getting started, make sure you have the following prerequisites installed:

- Node.js and npm: You can download them from [nodejs.org](https://nodejs.org/).
- Nest CLI: Install the Nest CLI globally using `npm install -g @nestjs/cli`.
- Auth0 account: You'll need to sign up for an Auth0 account at [auth0.com](https://auth0.com/) and create an application to obtain your Auth0 credentials.

## Getting Started

### Configuration

1. Clone the repository to your local machine:

   ```bash
   git clone https://github.com/danielvelastegui/auth-test.git
   ```
2. Navigate to the project folder:

   ```bash
    cd auth-test
    ```
3. Install the dependencies:
   ```bash
   npm install
   ```
4. Change data in .env file
   ```bash
   AUTH0_ISSUER_URL=yourdomain.auth0.com
   AUTH0_AUDIENCE=youraudience
   ``` 
### Run the application:
1. Run the application in development mode:
   ```bash
    npm run start:dev
    ```
2. Navigate to `http://localhost:3000` in your browser to 
view the application.

## Usage
### Protected Routes
The project includes an example protected route that requires authentication. 
You can find it in `src/app.controller.ts`.
```typescript
@Get()
@UseGuards(AuthGuard('jwt'))
getHello(): string {
  return this.appService.getHello();
}
```
To access the protected route, you need to include a valid JWT token in the
`Authorization` header of your HTTP request.
```http request
GET http://localhost:3000
Authorization: Bearer YOUR_JWT_TOKEN
```
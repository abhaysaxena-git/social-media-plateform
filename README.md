# Connectly – Social Media Platform

Connectly is a mini social media application built using HTML, CSS, JavaScript, Node.js, Express.js, and SQLite. Users can create accounts, share posts, connect with other users, and explore content.

**Live Demo:** [Connectly – Social Media Platform](https://social-media-plateform-1.onrender.com)

## Features

- User registration and login with password hashing and JWT authentication
- User profiles with bio and profile picture
- Create, edit, and delete posts
- Share photos and videos using media URLs
- Like posts and add comments
- Follow and unfollow other users
- Search users by name or username
- Search posts and explore content
- Responsive design for desktop and mobile
- SQLite database for storing users, posts, comments, likes, and follows
- Basic security using input validation, Helmet, and rate limiting

## Tech Stack

- **Frontend:** HTML, CSS, JavaScript
- **Backend:** Node.js, Express.js
- **Database:** SQLite
- **Authentication:** JWT and bcrypt

## Requirements

- Node.js 22.x
- npm
- VS Code (optional)

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/abhaysaxena-git/social-media-plateform.git
```

### 2. Open the project folder

```bash
cd social-media-plateform
```

### 3. Install dependencies

```bash
npm install
```

### 4. Set environment variables

Create a `.env` file in the project root and add:

```env
JWT_SECRET=your_long_random_secret
```

Replace the example value with a strong, random secret.

### 5. Start the application

```bash
npm start
```

Open `http://localhost:3000` in your browser.

The SQLite database is created automatically when the application starts.

## Deployment

The application is deployed on Render.

- **Build Command:** `npm install`
- **Start Command:** `npm start`
- **Environment Variable:** `JWT_SECRET`

**Live Website:** https://social-media-plateform-1.onrender.com

## Project Notes

- The application uses SQLite to store user and post data.
- Media can be shared through URLs. File upload support depends on the implemented version of the application.
- The Explore feed displays existing posts in a different order.
- The database may not persist across restarts on hosts with temporary filesystems. Persistent storage or a managed database is recommended for long-term use.

## Future Improvements

- Add reliable image and video uploads
- Improve database storage for deployment
- Add password reset and email verification
- Add notifications and more profile options

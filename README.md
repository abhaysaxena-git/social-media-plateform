# Connectly — Mini Social Media Platform

A responsive mini social media app built with **HTML, CSS, Vanilla JavaScript, Node.js, Express.js, and SQLite**.

## Features
- Register/login with bcrypt password hashing and JWT authentication
- User profiles with bio and profile-picture upload from your device gallery (max 2 MB)
- Create, edit, and delete your own posts
- Upload photos and videos from your device gallery (max 8 MB per file) or use a media URL
- Like/unlike posts; add comments and delete your own comments
- Follow/unfollow users; following and explore feeds
- Search people by name or username (the @username is shown in results) and search posts
- Explore feed displays posts in randomized order to help discover content
- Responsive desktop and mobile layout
- SQLite tables for users, posts, comments, likes, and follows
- Server-side ownership checks, input validation, Helmet security headers, and login/register rate limiting

## Media upload notes
Uploaded profile pictures and post media are stored as Base64 data in SQLite for this small demo project. For a production deployment, use object storage (such as S3 or Cloudinary) rather than storing large media files directly in the database. The Explore page randomizes existing community posts; it does not automatically download or generate outside content.

## Requirements
- Node.js 18 or newer
- npm
- VS Code (recommended)

## Run on Windows
1. Extract this ZIP and open the `connectly-social-platform` folder in VS Code.
2. Open **Terminal → New Terminal**.
3. Install packages:
   ```powershell
   npm install
   ```
4. Copy `.env.example` to a new file named `.env`. Set `JWT_SECRET` to a long random secret.
5. Start the server:
   ```powershell
   npm start
   ```
6. Open [http://localhost:3000](http://localhost:3000).

The `connectly.db` database is created automatically. Keep the terminal open while using the app; press `Ctrl+C` to stop it.

## Quick test checklist
1. Register two different accounts.
2. Create a post with account one.
3. Log in with account two, open People, and follow account one.
4. Like and comment on a post.
5. View a profile and check post/follower counts.
6. Edit/delete your own post and delete your own comment.
7. Try to delete another user's post; the server should reject it.

## API overview
Authenticated routes require `Authorization: Bearer <token>`.

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/auth/register` | Create account |
| POST | `/api/auth/login` | Login |
| GET / PUT | `/api/me` | Read/update own profile |
| GET | `/api/users?q=...` | Search users |
| GET | `/api/users/:id` | View profile |
| POST / DELETE | `/api/users/:id/follow` | Follow/unfollow |
| GET | `/api/posts?mode=following` | Following feed |
| GET | `/api/posts?mode=explore&q=...` | Explore/search posts |
| POST | `/api/posts` | Create post |
| PUT / DELETE | `/api/posts/:id` | Edit/delete own post |
| POST | `/api/posts/:id/like` | Toggle like |
| GET / POST | `/api/posts/:id/comments` | List/add comments |
| DELETE | `/api/comments/:id` | Delete own comment |
| GET | `/api/health` | Health check |

## Upload to GitHub
Create an empty repository on GitHub, then run these commands in the project folder:
```powershell
git init
git add .
git commit -m "Build Connectly social media platform"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```
Replace the example repository URL with your own. `.gitignore` excludes `.env`, `node_modules`, and SQLite files.

## Deploy on Render
1. Push the project to GitHub.
2. Create a Render **Web Service** and connect the repository.
3. Build command: `npm install`
4. Start command: `npm start`
5. Add environment variable `JWT_SECRET` with a long random secret.
6. Deploy and open the URL Render provides.

**Database persistence:** The SQLite database lives in `connectly.db` inside the project directory. Some free hosting filesystems are ephemeral, so data may be lost on restart or redeploy. For reliable long-term data, use persistent storage supported by your host or migrate to a managed database such as PostgreSQL.

## Demo limitations
- Avatar and post images use URLs; image file uploads are not included.
- No password reset, email verification, private accounts, real-time notifications, or payment features.
- This is a learning/demo project, not production-ready infrastructure. Keep dependencies updated and review security before accepting real users.

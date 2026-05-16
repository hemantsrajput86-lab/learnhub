# LearnHub 🎓
A free, open-source educational platform with community forums, courses, and user auth.

**Stack:** HTML · CSS · Vanilla JS · Node.js · Express · MongoDB · Render.com

---

## 🚀 Deploy for Free in 4 Steps

### Step 1 — Push to GitHub
1. Go to https://github.com and create a new **public** repository called `learnhub`
2. Upload all these files (drag & drop into GitHub, or use Git)

### Step 2 — Set up MongoDB Atlas (free database)
1. Go to https://mongodb.com/atlas and create a free account
2. Create a **free M0 cluster** (any region)
3. Under **Database Access** → Add a user with a username & password
4. Under **Network Access** → Add IP `0.0.0.0/0` (allow all, for Render)
5. Click **Connect** → **Drivers** → copy your connection string
   - It looks like: `mongodb+srv://USER:PASSWORD@cluster0.xxxxx.mongodb.net/learnhub?retryWrites=true&w=majority`

### Step 3 — Deploy on Render.com (free hosting)
1. Go to https://render.com and sign up with GitHub
2. Click **New → Web Service**
3. Connect your `learnhub` GitHub repository
4. Fill in:
   - **Name:** learnhub
   - **Runtime:** Node
   - **Build Command:** `npm install`
   - **Start Command:** `node server.js`
5. Under **Environment Variables**, add:
   - `MONGO_URI` → paste your Atlas connection string
   - `SESSION_SECRET` → type any random long string (e.g. `learnhub-super-secret-abc123xyz`)
6. Click **Create Web Service** — Render will build and deploy!
7. Your site will be live at: `https://learnhub.onrender.com` (or similar)

### Step 4 — Seed the courses
Once deployed, visit this URL once to add sample courses:
```
https://YOUR-APP.onrender.com/api/courses/seed
```

---

## 📁 Project Structure
```
learnhub/
├── server.js           ← Express app entry point
├── package.json
├── .env.example        ← Copy to .env for local dev
├── models/
│   ├── User.js         ← User schema (auth)
│   ├── Post.js         ← Forum posts & replies
│   └── Course.js       ← Courses
├── routes/
│   ├── auth.js         ← /api/auth (login, register, logout)
│   ├── posts.js        ← /api/posts (forum CRUD)
│   └── courses.js      ← /api/courses
└── public/
    ├── index.html      ← Homepage
    ├── css/style.css
    ├── js/app.js       ← Shared utilities
    └── pages/
        ├── forum.html
        ├── courses.html
        ├── login.html
        └── register.html
```

## 🛠 Local Development
```bash
cp .env.example .env
# Fill in your MONGO_URI in .env
npm install
npm run dev
# Visit http://localhost:3000
```

## 🔑 API Endpoints
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/auth/register | Create account |
| POST | /api/auth/login | Log in |
| POST | /api/auth/logout | Log out |
| GET | /api/auth/me | Current user |
| GET | /api/posts | All forum posts |
| POST | /api/posts | Create post (auth required) |
| POST | /api/posts/:id/like | Like a post |
| POST | /api/posts/:id/reply | Reply to post |
| PATCH | /api/posts/:id/solve | Mark as solved |
| GET | /api/courses | All courses |
| POST | /api/courses/seed | Seed sample courses |

## 📜 License
MIT — free to use, modify, and distribute.

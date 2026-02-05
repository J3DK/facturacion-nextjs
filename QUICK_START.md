# ⚡ Quick Start Guide

## Local Development (5 minutes)

### 1. Install Dependencies
```bash
npm install
```

### 2. Setup Database

Create a local PostgreSQL database or use Vercel Postgres:

```bash
# Copy environment file
cp .env.example .env.local

# Edit .env.local with your database URL
nano .env.local
```

### 3. Run Migrations
```bash
npx prisma migrate dev
```

### 4. Start Development Server
```bash
npm run dev
```

Visit: **http://localhost:3000**

---

## Default Test Credentials

After first run, you can register or use:
- Email: `test@example.com`
- Password: `Test1234!`

---

## Vercel Deployment (1 click)

### 1. Push to GitHub
```bash
git add .
git commit -m "Deploy to Vercel"
git push
```

### 2. Import on Vercel
- Visit https://vercel.com/new
- Select your GitHub repo
- Click Import

### 3. Add Environment Variables
```
DATABASE_URL=postgresql://...
DIRECT_URL=postgresql://...
JWT_SECRET=generate-random-secret
NEXTAUTH_SECRET=generate-random-secret
```

### 4. Deploy
Done! Your app is live ✨

---

## Google OAuth Setup

1. Go to Google Cloud Console
2. Create OAuth 2.0 credentials (Desktop application)
3. Add `http://localhost:3000/api/auth/callback/google` to Authorized redirect URIs
4. Copy Client ID and Secret
5. Add to `.env.local`:
   ```
   GOOGLE_CLIENT_ID=your-id
   GOOGLE_CLIENT_SECRET=your-secret
   ```
6. Restart dev server

---

## Common Commands

```bash
npm run dev              # Start dev server
npm run build           # Build for production
npm start              # Run production build
npm run prisma:studio  # Open Prisma database UI
npx prisma migrate dev # Create migration
```

---

## Troubleshooting

**Error: "Can't find module"**
```bash
rm -rf node_modules
npm install
```

**Database connection failed**
- Check DATABASE_URL in .env.local
- Ensure database is running
- Try: `psql -U postgres -d facturacion`

**Port 3000 already in use**
```bash
npm run dev -- -p 3001
```

---

## Project Structure

```
✅ Next.js 14 (App Router)
✅ Prisma 6 + PostgreSQL
✅ NextAuth (Google + Email)
✅ TailwindCSS + TypeScript
✅ API Routes + Server Actions
✅ User Profile Management
✅ Production Ready
```

---

**Start coding!** 🚀

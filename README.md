# Facturación App - Modern Invoicing Solution

A modern, production-ready invoicing application built with **Next.js 14**, **Prisma 6**, **NextAuth**, and **TailwindCSS**. Designed for deployment on Vercel with zero configuration.

## 🚀 Features

- ✅ **Next.js 14** (App Router)
- ✅ **Authentication** (Google OAuth + Credentials)
- ✅ **Prisma ORM** with PostgreSQL
- ✅ **Prisma Accelerate** for database acceleration
- ✅ **TailwindCSS** for styling
- ✅ **TypeScript** for type safety
- ✅ **Server Components** and **Server Actions**
- ✅ **Responsive Design** (Mobile-friendly)
- ✅ **User Profile Management**
- ✅ **Image Upload** (Avatar)
- ✅ **Password Management**
- ✅ **Account Deletion**

## 📋 Prerequisites

- Node.js 18+
- PostgreSQL database (or use Vercel PostgreSQL)
- Google OAuth credentials (optional)

## 🔧 Installation

### 1. Clone and Install

```bash
git clone <repository>
cd facturacion-nextjs
npm install
```

### 2. Configure Environment Variables

```bash
cp .env.example .env.local
```

Edit `.env.local`:

```env
# Database (Vercel PostgreSQL or local)
DATABASE_URL="postgresql://user:password@localhost:5432/facturacion"
DIRECT_URL="postgresql://user:password@localhost:5432/facturacion"

# NextAuth
JWT_SECRET="generate-a-random-secret"
NEXTAUTH_SECRET="generate-another-random-secret"

# Google OAuth (optional)
GOOGLE_CLIENT_ID="your-client-id"
GOOGLE_CLIENT_SECRET="your-client-secret"
```

### 3. Setup Database

```bash
npx prisma migrate dev
```

### 4. Run Development Server

```bash
npm run dev
```

Visit `http://localhost:3000`

## 🗂️ Project Structure

```
facturacion-nextjs/
├── app/
│   ├── api/
│   │   ├── auth/[...nextauth]/   # NextAuth configuration
│   │   └── users/profile/        # User API endpoints
│   ├── auth/
│   │   ├── login/                # Login page
│   │   └── register/             # Register page
│   ├── dashboard/                # Protected dashboard
│   ├── profile/                  # User profile page
│   ├── layout.tsx                # Root layout
│   ├── page.tsx                  # Home/login page
│   └── globals.css               # Global styles
├── components/
│   ├── LoginForm.tsx             # Login component
│   ├── RegisterForm.tsx          # Register component
│   └── ProfileCard.tsx           # Profile component
├── lib/
│   ├── prisma.ts                 # Prisma client singleton
│   └── auth.ts                   # NextAuth configuration
├── prisma/
│   └── schema.prisma             # Database schema
├── public/                       # Static files
├── .env.example                  # Environment variables template
├── next.config.js                # Next.js configuration
├── tailwind.config.js            # Tailwind configuration
├── postcss.config.js             # PostCSS configuration
├── tsconfig.json                 # TypeScript configuration
└── package.json                  # Dependencies

```

## 🔐 Authentication

### With Email (Credentials)

1. Register at `/auth/register`
2. Login at `/auth/login`
3. Password is hashed with bcryptjs

### With Google OAuth

1. Configure `GOOGLE_CLIENT_ID` and `GOOGLE_CLIENT_SECRET` in `.env.local`
2. Click "Sign in with Google"
3. Account is created automatically

## 📱 API Endpoints

### Authentication

- `POST /api/auth/register` - Register new user
- `POST /api/auth/[...nextauth]` - NextAuth endpoints

### User Profile

- `GET /api/users/profile` - Get user profile
- `PUT /api/users/profile` - Update name/avatar
- `POST /api/users/profile` - Change password
- `DELETE /api/users/profile` - Delete account

## 🎨 UI Components

- **LoginForm** - Email/password login
- **RegisterForm** - User registration
- **ProfileCard** - User profile management
  - Edit name
  - Upload avatar
  - Change password
  - Delete account
  - Sign out

## 🗄️ Database Schema

### Users Table

- `id` - UUID
- `email` - Unique email
- `password` - Hashed password (optional)
- `name` - Full name
- `image` - Avatar URL
- `emailVerified` - Email verification date
- `createdAt` - Creation timestamp

### Additional Tables

- `accounts` - OAuth accounts (Google)
- `sessions` - Active sessions
- `verification_tokens` - Email verification tokens
- `clientes` - Customers
- `conceptos` - Products/Services
- `facturas` - Invoices
- `items_factura` - Invoice items
- `configuracion` - User company configuration

## 🚀 Deployment (Vercel)

### 1. Push to GitHub

```bash
git add .
git commit -m "Initial commit"
git push origin main
```

### 2. Deploy to Vercel

1. Visit https://vercel.com
2. Import your GitHub repository
3. Set environment variables:
   - `DATABASE_URL` - Your PostgreSQL URL
   - `DIRECT_URL` - Direct connection URL
   - `JWT_SECRET` - Random secret
   - `NEXTAUTH_SECRET` - Random secret
   - `GOOGLE_CLIENT_ID` - (optional)
   - `GOOGLE_CLIENT_SECRET` - (optional)
4. Click Deploy

### 3. Setup Database

After deployment, run:

```bash
npx prisma migrate deploy
```

## 🔒 Security

- Passwords hashed with bcryptjs (10 rounds)
- JWT tokens with expiration
- NextAuth session management
- CORS configured for Vercel
- Environment variables secured
- SQL injection prevention (Prisma ORM)

## 📦 Dependencies

- **next** 14.2.28 - React framework
- **react** 18.2.0 - UI library
- **prisma** 6.7.0 - ORM
- **next-auth** 4.24.11 - Authentication
- **tailwindcss** 3.3.3 - CSS framework
- **bcryptjs** 2.4.3 - Password hashing
- **zod** 3.23.8 - Schema validation
- **swr** 2.2.4 - Data fetching

## 🛠️ Scripts

```bash
npm run dev              # Development server
npm run build           # Production build
npm start              # Start production server
npm run lint           # Run ESLint
npm run prisma:generate # Generate Prisma client
npm run prisma:migrate  # Run migrations
npm run prisma:studio   # Open Prisma Studio
```

## 🐛 Troubleshooting

### Database Connection Error

Ensure `DATABASE_URL` is correct and database is running.

### NextAuth Issues

- Clear `.next` folder: `rm -rf .next`
- Regenerate Prisma client: `npx prisma generate`

### Build Errors

```bash
rm -rf node_modules
npm install
npm run build
```

## 📝 License

MIT

## 🤝 Support

For issues or questions, please open an issue on GitHub.

---

**Ready for production** ✅ | **Optimized for Vercel** ✅ | **Zero config deployment** ✅

# 💰 Personal Finance Tracker

A modern, full-stack personal finance management application built with Next.js 15, TypeScript, and Supabase. Track your income, expenses, and financial goals with beautiful analytics and insights tailored for Sri Lankan users.

![Finance Tracker](https://img.shields.io/badge/Next.js-15.3.3-black?style=for-the-badge&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5.8.3-blue?style=for-the-badge&logo=typescript)
![Supabase](https://img.shields.io/badge/Supabase-PostgreSQL-green?style=for-the-badge&logo=supabase)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-4.1.10-38B2AC?style=for-the-badge&logo=tailwind-css)
![React](https://img.shields.io/badge/React-19.0.0-61DAFB?style=for-the-badge&logo=react)

## 🌟 Features

### 🔐 Authentication System
- **User Registration & Login** - Secure authentication with form validation using Zod schemas
- **Protected Routes** - Automatic redirection for unauthorized access with ProtectedRoute component
- **Session Management** - Persistent login state with localStorage and React Context
- **Professional UI** - Clean, modern authentication forms with error handling
- **Demo Mode** - Quick demo access for testing (email: any@email.com, password: 6+ chars)

### 📊 Financial Management
- **Transaction Tracking** - Add, edit, delete income and expense transactions with full CRUD operations
- **Category Management** - 40+ pre-defined Sri Lankan categories with emojis and color coding
- **Real-time Dashboard** - Live financial overview with key metrics and recent transactions
- **Advanced Filtering** - Filter transactions by type, category, date range, and description
- **Sri Lankan Context** - LKR currency, local categories (Rice & Curry, CEB Bills, Dialog/Mobitel, etc.)
- **Data Validation** - Form validation with Zod for data integrity and user experience

### 📈 Analytics & Insights
- **Interactive Charts** - Beautiful pie charts and bar graphs using Recharts
- **Expense Breakdown** - Visual representation of spending by category
- **Income Analysis** - Track income sources and patterns
- **Monthly Trends** - Historical data visualization for the last 6 months
- **Financial Summaries** - Total income, expenses, and net balance

### 🎨 User Experience
- **Responsive Design** - Optimized for desktop, tablet, and mobile devices
- **Modern UI Components** - Custom-built components with TailwindCSS
- **Loading States** - Smooth loading indicators and error handling
- **Sri Lankan Context** - LKR currency and localized categories

## 🛠️ Tech Stack

### Frontend
- **[Next.js 15.3.3](https://nextjs.org/)** - React framework with App Router and Turbopack
- **[React 19.0.0](https://react.dev/)** - Latest React with concurrent features
- **[TypeScript 5.8.3](https://www.typescriptlang.org/)** - Type-safe JavaScript with strict mode
- **[TailwindCSS 4.1.10](https://tailwindcss.com/)** - Utility-first CSS framework with custom theme
- **[Recharts 2.15.3](https://recharts.org/)** - Composable charting library for data visualization
- **[Lucide React 0.514.0](https://lucide.dev/)** - Beautiful SVG icon library
- **[Date-fns 4.1.0](https://date-fns.org/)** - Modern JavaScript date utility library
- **[Zod 3.25.63](https://zod.dev/)** - TypeScript-first schema validation

### Backend & Database
- **[Supabase](https://supabase.com/)** - PostgreSQL database with real-time features and REST API
- **[Supabase Auth](https://supabase.com/auth)** - Authentication and user management with JWT
- **[Supabase Auth Helpers](https://supabase.com/docs/guides/auth/auth-helpers/nextjs)** - Next.js integration for seamless auth
- **Row Level Security (RLS)** - Database-level security policies for data isolation
- **PostgreSQL** - Robust relational database with ACID compliance

### Development Tools
- **[ESLint 9](https://eslint.org/)** - Code linting with Next.js and TypeScript rules
- **[PostCSS 8.5.5](https://postcss.org/)** - CSS processing with Tailwind integration
- **[Autoprefixer 10.4.21](https://autoprefixer.github.io/)** - CSS vendor prefixing for browser compatibility

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ and npm/yarn/pnpm
- Supabase account and project

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/personal-finance-tracker.git
cd personal-finance-tracker
```

### 2. Install Dependencies
```bash
npm install
# or
yarn install
# or
pnpm install
```

### 3. Environment Setup
Create a `.env.local` file in the root directory:
```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
```

### 4. Database Setup
Run the SQL scripts in your Supabase Dashboard → SQL Editor in this order:

1. **Initial Setup**: Execute `database-setup.sql`
   - Creates `categories` and `transactions` tables
   - Sets up Row Level Security (RLS) policies
   - Creates indexes for optimal performance
   - Inserts 40+ Sri Lankan categories

2. **RLS Policy Fixes** (if needed): Execute `fix-rls-policies.sql`
   - Fixes any RLS policy issues for development
   - Allows demo data access
   - Configures proper user permissions

### 5. Start Development Server
```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) to view the application.

## 📁 Project Structure

```
personal-finance-tracker/
├── src/
│   ├── app/                    # Next.js 15 App Router pages
│   │   ├── analytics/         # Analytics dashboard with charts
│   │   │   └── page.tsx       # Analytics page component
│   │   ├── dashboard/         # Main financial dashboard
│   │   │   └── page.tsx       # Dashboard overview
│   │   ├── login/            # Authentication pages
│   │   │   └── page.tsx      # Login form
│   │   ├── register/         # User registration
│   │   │   └── page.tsx      # Registration form
│   │   ├── transactions/     # Transaction management
│   │   │   ├── add/          # Add new transaction
│   │   │   │   └── page.tsx  # Transaction form
│   │   │   ├── [id]/         # Dynamic transaction routes
│   │   │   │   └── edit/     # Edit transaction
│   │   │   │       └── page.tsx
│   │   │   └── page.tsx      # Transaction list
│   │   ├── globals.css       # Global styles with Tailwind
│   │   ├── layout.tsx        # Root layout with providers
│   │   └── page.tsx          # Landing page
│   ├── components/            # Reusable UI components
│   │   ├── ui/               # Base UI components
│   │   │   ├── Button.tsx    # Custom button variants
│   │   │   ├── Card.tsx      # Container component
│   │   │   └── Input.tsx     # Form input with validation
│   │   ├── Header.tsx        # Navigation header
│   │   └── ProtectedRoute.tsx # Route protection HOC
│   ├── contexts/             # React Context providers
│   │   └── AuthContext.tsx   # Authentication state management
│   ├── lib/                  # Utility libraries
│   │   ├── supabase.ts      # Supabase client & database types
│   │   ├── utils.ts         # Helper functions
│   │   ├── validations.ts   # Zod validation schemas
│   │   └── sri-lankan-data.ts # Local data and constants
│   └── types/               # TypeScript type definitions
│       └── transaction.ts   # Transaction-related interfaces
├── public/                   # Static assets
│   ├── favicon.ico          # App favicon
│   └── *.svg               # Icon assets
├── database-setup.sql       # Initial database schema
├── fix-rls-policies.sql    # RLS policy configurations
├── package.json            # Dependencies and scripts
├── tsconfig.json           # TypeScript configuration
├── next.config.ts          # Next.js configuration
├── postcss.config.mjs      # PostCSS configuration
├── eslint.config.mjs       # ESLint configuration
└── README.md              # Project documentation
```

## 🗄️ Database Schema

### Categories Table
```sql
CREATE TABLE categories (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(100) NOT NULL,
  icon VARCHAR(10) NOT NULL,
  color VARCHAR(7) NOT NULL,
  type VARCHAR(10) CHECK (type IN ('income', 'expense')),
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);
```

### Transactions Table
```sql
CREATE TABLE transactions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES auth.users(id) ON DELETE CASCADE,
  amount DECIMAL(12,2) NOT NULL CHECK (amount > 0),
  type VARCHAR(10) NOT NULL CHECK (type IN ('income', 'expense')),
  category_id UUID REFERENCES categories(id),
  description TEXT NOT NULL,
  date DATE NOT NULL,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);
```

## 🔧 Key Components

### Authentication Context
Manages user authentication state across the application:
- Login/logout functionality
- User session persistence
- Protected route access control

### Database Layer
Abstracted database operations with TypeScript:
- CRUD operations for transactions
- Category management
- Analytics data aggregation
- Type-safe database queries

### UI Components
Reusable, accessible components:
- **Button**: Multiple variants and sizes
- **Card**: Consistent container styling
- **Input**: Form inputs with validation
- **Header**: Navigation with user context

## 📊 Analytics Features

### Dashboard Metrics
- Total income and expenses
- Current balance calculation
- Transaction count
- Recent transactions list

### Visual Analytics
- **Pie Charts**: Expense and income breakdown by category
- **Bar Charts**: Monthly trends over time
- **Category Lists**: Detailed breakdown with percentages
- **Time Filtering**: View data for different time periods

## 🔒 Security Features

### Authentication & Authorization
- **Form Validation** - Client-side validation with Zod schemas and server-side verification
- **Password Security** - Minimum 6 characters requirement with secure hashing
- **Session Management** - JWT-based authentication with automatic token refresh
- **Protected Routes** - Route-level protection with automatic redirects
- **User Context** - Secure user state management with React Context API

### Database Security
- **Row Level Security (RLS)** - PostgreSQL RLS policies ensuring users only access their own data
- **User Isolation** - UUID-based user identification with foreign key constraints
- **SQL Injection Prevention** - Parameterized queries and Supabase client protection
- **Secure API Endpoints** - Server-side validation and authentication checks
- **Data Encryption** - Encrypted data transmission with HTTPS and secure storage

### Privacy & Compliance
- **Data Minimization** - Only collect necessary financial data
- **User Control** - Users can delete their own transactions and data
- **Secure Storage** - Encrypted database storage with Supabase infrastructure
- **No Third-party Tracking** - Privacy-focused design without external analytics

## 🎨 Design System

### Color Palette
- **Primary**: Blue (#3B82F6)
- **Success**: Green (#10B981)
- **Danger**: Red (#EF4444)
- **Warning**: Yellow (#F59E0B)
- **Neutral**: Gray scale

### Typography
- **Font**: Geist Sans (Vercel's font family)
- **Headings**: Bold, hierarchical sizing
- **Body**: Regular weight, readable line height

### Components
- Consistent spacing using Tailwind's scale
- Rounded corners and subtle shadows
- Hover and focus states for interactivity
- Mobile-first responsive design

## 🚀 Deployment

### Vercel (Recommended)
1. **Connect Repository**: Link your GitHub repository to Vercel
2. **Environment Variables**: Add the following in Vercel dashboard:
   ```
   NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
   ```
3. **Auto Deploy**: Automatic deployment on push to main branch
4. **Custom Domain**: Configure custom domain in Vercel settings

### Manual Deployment
```bash
# Build the application
npm run build

# Start production server
npm run start

# Or using PM2 for production
npm install -g pm2
pm2 start npm --name "finance-tracker" -- start
```

### Docker Deployment
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "start"]
```

## 🧪 Testing

### Running Tests
```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm run test:coverage
```

### Test Structure
- **Unit Tests** - Component and utility function testing
- **Integration Tests** - API endpoint and database operation testing
- **E2E Tests** - Full user workflow testing with Playwright

## 📊 Performance

### Optimization Features
- **Next.js 15** - Latest performance optimizations and Turbopack
- **Image Optimization** - Automatic image optimization with Next.js Image component
- **Code Splitting** - Automatic code splitting for optimal loading
- **Static Generation** - Pre-rendered pages for better performance
- **Database Indexing** - Optimized database queries with proper indexing

### Monitoring
- **Core Web Vitals** - Optimized for Google's Core Web Vitals
- **Bundle Analysis** - Regular bundle size monitoring
- **Database Performance** - Query optimization and connection pooling

## 🤝 Contributing

We welcome contributions! Please follow these steps:

### Development Setup
1. **Fork the repository** and clone your fork
2. **Install dependencies**: `npm install`
3. **Set up environment**: Copy `.env.example` to `.env.local`
4. **Database setup**: Run the SQL scripts in Supabase
5. **Start development**: `npm run dev`

### Contribution Guidelines
1. **Create a feature branch**: `git checkout -b feature/amazing-feature`
2. **Follow code style**: Use ESLint and Prettier configurations
3. **Write tests**: Add tests for new features
4. **Update documentation**: Update README if needed
5. **Commit changes**: Use conventional commit messages
6. **Push to branch**: `git push origin feature/amazing-feature`
7. **Open Pull Request**: Provide clear description of changes

### Code Style
- Use TypeScript for all new code
- Follow ESLint and Prettier configurations
- Use meaningful variable and function names
- Add JSDoc comments for complex functions
- Maintain consistent file structure

## 🐛 Troubleshooting

### Common Issues

#### Database Connection Issues
```bash
# Check environment variables
echo $NEXT_PUBLIC_SUPABASE_URL
echo $NEXT_PUBLIC_SUPABASE_ANON_KEY

# Verify Supabase connection
npm run test:db
```

#### Build Errors
```bash
# Clear Next.js cache
rm -rf .next

# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install

# Check TypeScript errors
npm run type-check
```

#### Authentication Issues
- Verify Supabase Auth is enabled
- Check RLS policies are correctly configured
- Ensure environment variables are set correctly


### Version History
- **v0.1.0** - Initial release with basic transaction tracking
- **v0.2.0** - Added analytics and charts
- **v0.3.0** - Enhanced security and authentication
- **v1.0.0** - Production-ready release (planned)



## � Acknowledgments

- **[Next.js](https://nextjs.org/)** - For the amazing React framework with App Router
- **[Supabase](https://supabase.com/)** - For the powerful backend infrastructure and PostgreSQL
- **[TailwindCSS](https://tailwindcss.com/)** - For the utility-first CSS framework
- **[Recharts](https://recharts.org/)** - For the beautiful and responsive charting library
- **[Lucide](https://lucide.dev/)** - For the comprehensive icon library
- **[Vercel](https://vercel.com/)** - For the seamless deployment platform
- **[TypeScript](https://www.typescriptlang.org/)** - For type safety and developer experience
- **Sri Lankan Developer Community** - For inspiration and local context



Demo
![a7](https://github.com/user-attachments/assets/b6bb4412-f916-42aa-a1bc-c2c4071bb11c)
![a1](https://github.com/user-attachments/assets/c36a7738-58e2-4f71-8833-540688dd0b19)
![a2](https://github.com/user-attachments/assets/a519ec59-e254-47e5-8e32-c49f6991f3af)
![a3](https://github.com/user-attachments/assets/71928693-ab5d-4e6c-9b7c-68655a04b265)
![a4](https://github.com/user-attachments/assets/70dd6e27-dc86-4d8f-8ad2-df112dbc8efd)
![a5](https://github.com/user-attachments/assets/a3e00a20-b514-4be4-add3-fbebb262a46e)
![a6](https://github.com/user-attachments/assets/b680491e-fe4e-4527-8594-99fec3d8e3be)

Supabase
![db1](https://github.com/user-attachments/assets/9f0455dd-a612-45af-8213-4eacf5bf51b3)
![db2](https://github.com/user-attachments/assets/c5c63da9-7b47-4793-9999-821826025fc7)
![db3](https://github.com/user-attachments/assets/7e671d1f-141e-4099-a1b4-e5ba9e560d79)
![db4](https://github.com/user-attachments/assets/891a12e9-b4eb-4f49-872b-4c07cca27ddc)


⭐ **Star this repository if you found it helpful!**



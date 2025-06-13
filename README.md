# 💰 Personal Finance Tracker

A modern, full-stack personal finance management application built with Next.js 15, TypeScript, and Supabase. Track your income, expenses, and financial goals with beautiful analytics and insights.

![Finance Tracker](https://img.shields.io/badge/Next.js-15.3.3-black?style=for-the-badge&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue?style=for-the-badge&logo=typescript)
![Supabase](https://img.shields.io/badge/Supabase-Database-green?style=for-the-badge&logo=supabase)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-4.1.10-38B2AC?style=for-the-badge&logo=tailwind-css)

## 🌟 Features

### 🔐 Authentication System
- **User Registration & Login** - Secure authentication with form validation
- **Protected Routes** - Automatic redirection for unauthorized access
- **Session Management** - Persistent login state with localStorage
- **Professional UI** - Clean, modern authentication forms

### 📊 Financial Management
- **Transaction Tracking** - Add, edit, delete income and expense transactions
- **Category Management** - Organized spending categories with icons and colors
- **Real-time Dashboard** - Live financial overview with key metrics
- **Advanced Filtering** - Filter transactions by type, category, and date range

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
- **[Next.js 15](https://nextjs.org/)** - React framework with App Router
- **[TypeScript](https://www.typescriptlang.org/)** - Type-safe JavaScript
- **[TailwindCSS 4.1](https://tailwindcss.com/)** - Utility-first CSS framework
- **[Recharts](https://recharts.org/)** - Composable charting library
- **[Lucide React](https://lucide.dev/)** - Beautiful icon library

### Backend & Database
- **[Supabase](https://supabase.com/)** - PostgreSQL database with real-time features
- **[Supabase Auth](https://supabase.com/auth)** - Authentication and user management
- **Row Level Security (RLS)** - Database-level security policies

### Development Tools
- **[ESLint](https://eslint.org/)** - Code linting and formatting
- **[PostCSS](https://postcss.org/)** - CSS processing
- **[Autoprefixer](https://autoprefixer.github.io/)** - CSS vendor prefixing

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
Run the SQL scripts in your Supabase Dashboard → SQL Editor:

1. **Initial Setup**: Execute `database-setup.sql`
2. **RLS Policies**: Execute `fix-rls-policies.sql`
3. **Sample Data** (Optional): Execute `add-sample-data.sql`

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
src/
├── app/                    # Next.js App Router pages
│   ├── (auth)/
│   │   ├── login/         # Login page
│   │   └── register/      # Registration page
│   ├── dashboard/         # Main dashboard
│   ├── transactions/      # Transaction management
│   │   ├── add/          # Add transaction form
│   │   └── [id]/edit/    # Edit transaction form
│   ├── analytics/         # Analytics and charts
│   └── api/              # API routes
├── components/            # Reusable UI components
│   ├── ui/               # Base UI components
│   │   ├── Button.tsx    # Custom button component
│   │   ├── Card.tsx      # Card container component
│   │   └── Input.tsx     # Form input component
│   ├── Header.tsx        # Navigation header
│   └── ProtectedRoute.tsx # Route protection wrapper
├── contexts/             # React contexts
│   └── AuthContext.tsx   # Authentication state management
├── lib/                  # Utility libraries
│   ├── supabase.ts      # Database client and functions
│   ├── utils.ts         # Helper functions
│   └── validations.ts   # Form validation schemas
└── types/               # TypeScript type definitions
    └── transaction.ts   # Transaction-related types
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

### Authentication
- Form validation with error handling
- Secure password requirements
- Session management
- Automatic logout on token expiry

### Database Security
- Row Level Security (RLS) policies
- User-specific data access
- SQL injection prevention
- Secure API endpoints

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
1. Connect your GitHub repository to Vercel
2. Add environment variables in Vercel dashboard
3. Deploy automatically on push to main branch

### Manual Deployment
```bash
npm run build
npm run start
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Next.js](https://nextjs.org/) for the amazing React framework
- [Supabase](https://supabase.com/) for the backend infrastructure
- [TailwindCSS](https://tailwindcss.com/) for the utility-first CSS framework
- [Recharts](https://recharts.org/) for the beautiful charting library
- [Lucide](https://lucide.dev/) for the icon library

## 📧 Contact

**Your Name** - your.email@example.com

Project Link: [https://github.com/yourusername/personal-finance-tracker](https://github.com/yourusername/personal-finance-tracker)

---

⭐ **Star this repository if you found it helpful!**

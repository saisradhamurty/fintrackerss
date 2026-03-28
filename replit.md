# Fintracker AI – Financial Wellness Coach for Students

## Overview
A complete AI-powered mobile application for student financial wellness. Built with Expo React Native + Express backend + PostgreSQL database + OpenAI GPT-5.2.

## Stack
- **Monorepo tool**: pnpm workspaces
- **Mobile**: Expo React Native (SDK 54) with Expo Router
- **Backend**: Node.js + Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **AI**: OpenAI GPT-5.2 via Replit AI Integrations (no API key needed)

## Demo Account
- Email: demo@test.com
- Password: password123

## Features

### Core
1. **User Authentication** – Register/login with JWT tokens
2. **Expense Tracking** – Manual input with AI auto-categorization (NLP)
3. **Real-time Dashboard** – Bar charts, category breakdown, recent transactions
4. **Analytics** – Week/month/year periods, spending trends, savings rate
5. **Budget Management** – Set per-category budgets, track overspending
6. **Discipline Score** – AI-calculated score (0–100) with grade breakdown
7. **AI Chat (Finn)** – Streaming GPT-5.2 financial coach with quick prompts
8. **AI Insights** – GPT-generated personalized financial recommendations

### Advanced AI Features
9. **Financial Personality Detection** – Saver / Spender / Risky classification based on transaction history
10. **Predictive Spending Alerts** – "You may exceed budget in X days" using daily rate projection
11. **Goal-Based Savings System** – Create savings goals, track progress, contribute amounts, deadline tracking
12. **Emotional Spending Detection** – Late-night (10PM+) and weekend spending pattern detection
13. **Gamification System** – Badges (First Step, Smart Saver, Budget Master, etc.), day streaks, levels, XP points
14. **"What If" Simulator** – Hypothetical savings calculator with line-graph projection (up to 5 years)
15. **Real-time Notification System** – Budget exceeded, predictive risk, goal completion, achievement alerts

## App Screens
- **Auth** – Login / Sign Up with demo credentials shown
- **Home Dashboard** – All widgets: personality badge, urgent alerts, spending chart, categories, achievements, goals, score, emotional insight, simulator button, AI insights
- **Add Expense** – Amount + description, AI auto-categorize, quick sample buttons
- **AI Chat (Finn)** – Streaming chat with quick financial prompts
- **Alerts** – Full notification panel with severity indicators, mark read, type labels
- **Profile** – Tabs: Transactions, Budgets, Goals, Badges + Sign Out

## Database Tables
- `users` – Auth + monthly income
- `expenses` – All transactions
- `budgets` – Per-category monthly limits
- `insights` – Generated AI insight records
- `user_personality` – Saver/Spender/Risky classification
- `goals` – Savings goals with progress and deadlines
- `badges` – Earned badges per user (unique userId+badgeKey)
- `streaks` – Daily streaks, level, total XP points
- `notifications` – Alert storage (overspend, predictive, emotional, achievement)

## API Endpoints
### Auth
- `POST /api/auth/register` / `POST /api/auth/login` / `GET /api/auth/me`

### Core
- `GET/POST/DELETE /api/expenses`
- `GET /api/analytics/summary?period=week|month|year`
- `GET /api/analytics/discipline-score`
- `GET/POST /api/budgets`
- `GET /api/insights`
- `POST /api/openai/chat` (SSE streaming)
- `POST /api/openai/categorize`
- `POST /api/openai/generate-insights`

### Advanced Features
- `GET /api/personality` – Compute & return financial personality
- `GET/POST /api/goals` – Savings goals CRUD
- `PATCH /api/goals/:id/contribute` – Add contribution to a goal
- `GET /api/gamification` – Full gamification status
- `POST /api/gamification/checkin` – Daily streak check-in
- `POST /api/gamification/award` – Award a badge
- `GET /api/notifications` – Fetch notifications
- `POST /api/notifications/generate` – Generate AI-driven alerts
- `PATCH /api/notifications/:id/read` / `PATCH /api/notifications/read-all`
- `POST /api/simulator/whatif` – Project savings over time
- `GET /api/simulator/emotional` – Detect emotional spending patterns

## Design
- Background: `#0A0A0F`, Card: `#1A1A26`, Primary: `#00D4AA` (teal)
- Danger: `#FF6B6B`, Warning: `#FFB347`, Purple: `#6366F1`
- Font: Inter (400/500/600/700)
- Tab bar: NativeTabs with Liquid Glass on iOS 26+, BlurView on iOS, solid on web

## Environment Variables
- `DATABASE_URL` – PostgreSQL (auto-provisioned)
- `AI_INTEGRATIONS_OPENAI_BASE_URL` / `AI_INTEGRATIONS_OPENAI_API_KEY` – Replit AI proxy
- `EXPO_PUBLIC_DOMAIN` – Injected at build time for API calls

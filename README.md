# Finwise AI (AI Money Mentor)

Finwise AI is a premium personal finance and budgeting web application specifically designed for the Indian demographic. It helps users overcome financial illiteracy by providing a consolidated dashboard of their finances and personalized, actionable advice via a built-in AI chatbot.

## 🚀 Key Features

- **Personalized Onboarding**: Tailored setup flow to capture income, expenses, financial goals, and risk profiles.
- **Interactive Dashboard**: Visualize your financial health with a "Money Health Score," expense breakdowns, and 6-month trends.
- **AI Money Mentor**: A knowledgeable AI coach for Indian markets, providing guidance on SIP, PPF, NPS, ELSS, and more.
- **Investment Recommendations**: Smart asset allocation based on your individual risk appetite (Conservative, Moderate, Aggressive).
- **Secure by Design**: Row Level Security (RLS) ensures your data is private, and AI keys are securely handled via Edge Functions.
- **Offline Resilience**: Graceful fallbacks to local storage ensure the app remains functional even with connectivity issues.

## 🛠️ Tech Stack

- **Frontend**: [React 18](https://reactjs.org/), [Vite](https://vitejs.dev/), [TypeScript](https://www.typescriptlang.org/)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/), [Shadcn UI](https://ui.shadcn.com/)
- **Charts**: [Recharts](https://recharts.org/)
- **Backend & Auth**: [Supabase](https://supabase.com/) (Postgres + Auth + Edge Functions)
- **AI**: Google Gemini (via Lovable AI Gateway)

## 🏗️ Architecture

The project follows a modern SPA architecture:
- **Client**: Handles routing, data visualization, and state management.
- **Database**: Supabase Postgres with RLS policies to protect user-specific data.
- **Edge Functions**: Securely proxies AI requests, protecting sensitive API keys and managing system prompts.

## 📁 Project Structure

```text
src/
├── components/ui/   # Reusable Shadcn UI components
├── hooks/           # Custom React hooks
├── lib/             # Supabase client and financial utilities
├── pages/           # Core views (Dashboard, Chat, Onboarding, Auth)
└── App.tsx          # Main application routing
supabase/
├── functions/       # AI Chat Edge Function
└── migrations/      # Database schema and RLS policies
```

## 🤖 AI Money Mentor Logic

The AI Chatbot uses a specialized workflow to ensure high-quality financial advice:
1. **Trigger**: User interacts with the chat interface.
2. **Edge Proxy**: Requests are sent to a Supabase Edge Function which attaches a secure API key and a strict system prompt tailored for Indian personal finance.
3. **LLM**: The `google/gemini-3-flash-preview` model processes the query.
4. **Streaming**: Responses are streamed back to the user in real-time using Server-Sent Events (SSE).

---

*Disclaimer: The AI advice provided is for educational purposes. Users should consult a SEBI-registered advisor for personalized financial decisions.*

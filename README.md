# Full Stack AI Career Coach with Next JS, Neon DB, Tailwind, Prisma, Inngest, Shadcn UI  🔥🔥



A
# 🌟 AI-Powered Career Insights Platform

An intelligent platform that provides users with personalized career guidance, including salary expectations, top skills, industry growth outlook, and more — powered by **Google Gemini AI** and built using **Next.js**, **Clerk**, **PostgreSQL**, and **Prisma**.

---

## 🚀 Features

- 🔐 **User Authentication:** Secure login and signup using Clerk.
- 🎯 **Personalized Onboarding:** Users select their industry, experience level, and input their bio and skills.
- 🤖 **AI Industry Insights:**
  - Salary ranges for top roles
  - Skill demand levels (HIGH, MEDIUM, LOW)
  - Industry growth rates
  - Top and recommended skills
  - Market outlook (POSITIVE, NEUTRAL, NEGATIVE)
  - Key trends
- 🧠 **AI Integration:** Uses Google Gemini API to dynamically generate insights in structured JSON format.
- 💾 **Data Persistence:** Industry insights are cached in PostgreSQL using Prisma to reduce redundant AI calls.
- 🔁 **Smart Reusability:** If insights for an industry already exist, they are reused — saving cost and time.

---

## 🛠️ Tech Stack

| Layer        | Technology                  |
|--------------|-----------------------------|
| Frontend     | Next.js (App Router)        |
| Authentication | Clerk                     |
| Backend Logic| Server Actions (Next.js)    |
| Database     | PostgreSQL + Prisma ORM     |
| AI Service   | Google Gemini (Generative AI) |
| Language     | TypeScript / JavaScript     |

---

## 🧩 Project Structure

```
/app
  /onboarding      - User onboarding form
  /dashboard       - Displays industry insights
/lib
  /utils           - Utility functions for validation, formatting
  /ai              - AI helper for calling Google Gemini API
/prisma
  schema.prisma    - Prisma DB models for User & IndustryInsight
```

---

## 🧠 AI Prompt Structure

The prompt sent to Gemini API is formatted to ensure JSON-only responses:

```text
"You are an AI Career Coach. Based on the industry: {industry}, generate a detailed JSON object with fields:
- salaryRange
- topSkills
- recommendedSkills
- industryGrowthRate
- demandLevel (HIGH, MEDIUM, LOW)
- marketOutlook (POSITIVE, NEUTRAL, NEGATIVE)
- keyTrends

Return JSON only."
```

---

## 📦 Database Models

### `User`
| Field         | Type         | Description                     |
|---------------|--------------|---------------------------------|
| id            | String       | Clerk user ID                   |
| name          | String       | Full name                       |
| email         | String       | Email address                   |
| bio           | String       | Short bio                       |
| experience    | String       | User experience (e.g. Fresher)  |
| skills        | String[]     | Skills selected                 |
| industry      | String       | Selected industry               |
| insightId     | FK           | Links to `IndustryInsight`     |

---

### `IndustryInsight`
| Field             | Type         | Description                          |
|------------------|--------------|--------------------------------------|
| id               | String       | Unique identifier                    |
| industry          | String       | Industry name                        |
| salaryRange       | String[]     | Min and Max salary range             |
| topSkills         | String[]     | Most in-demand skills                |
| recommendedSkills | String[]     | Skills to improve or learn           |
| industryGrowthRate| String       | Annual growth %                      |
| demandLevel       | Enum         | HIGH, MEDIUM, LOW                    |
| marketOutlook     | Enum         | POSITIVE, NEUTRAL, NEGATIVE          |
| keyTrends         | String[]     | Emerging trends                      |

---


## 🔐 Authentication with Clerk

- Users are authenticated using Clerk.
- Clerk provides session management, user profiles, and secure endpoints.

---


### Make sure to create a `.env` file with following variables -

```
DATABASE_URL=

NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
CLERK_SECRET_KEY=

NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/onboarding
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/onboarding

GEMINI_API_KEY=
```


## ⚙️ Installation & Setup

1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-username/ai-career-coach.git
   cd ai-career-coach
   ```

2. **Install Dependencies**
   ```bash
   npm install
   ```

3. **Set up Environment Variables**
   Create a `.env` file:
   ```
   DATABASE_URL=your_postgres_url
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_public_key
   CLERK_SECRET_KEY=your_clerk_secret
   GEMINI_API_KEY=your_google_gemini_key
   ```

4. **Push Prisma Schema**
   ```bash
   npx prisma db push
   ```

5. **Run the Development Server**
   ```bash
   npm run dev
   ```

---

## 💡 Future Enhancements

- 📄 AI-based resume and cover letter generator
- 📊 Graphical dashboard with charts for salary & growth
- 🔔 Notifications for industry trend updates
- 📚 Personalized course recommendations for skill gaps

---

## 👨‍💻 Author

**Himanshi**  
B.Tech Student | Flutter & AI Enthusiast | Entrepreneur  
[LinkedIn](https://www.linkedin.com) • [GitHub](https://github.com)

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).
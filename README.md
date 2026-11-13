# NutriLife

A nutrition and fitness tracker aimed at Indian, vegetarian diets. You log meals (by photo or by hand), see daily and weekly calories and macros, get a diet plan, and get workout suggestions.

Built for the **Triveni hackathon**, where it placed **2nd**.

## Features

- **Meal logging:** manual entry, or a photo sent to Google Gemini to estimate calories, protein, carbs and fat.
- **Health score and swaps:** each meal gets a 1–10 score, and fried or processed foods get a healthier swap from a built-in list (rule-based, in `api/services/coach_logic.py`).
- **Diet plans:** create and save several vegetarian plans; the active plan sets your daily calorie goal.
- **Insights:** rule-based daily insights, exercise minutes needed to burn off a surplus, and a 30-day weight projection (7,700 kcal ≈ 1 kg).
- **Workouts, water tracking, meal reminders, and a nutrition chatbot** (Gemini).
- **Accounts** with JWT login.

## Tech

- **Backend:** Django, Django REST Framework, SimpleJWT, Pillow, Google GenAI SDK
- **Frontend:** React 19, TypeScript, Vite, Tailwind CSS, shadcn/ui, Framer Motion
- **Database:** SQLite

## Project layout

```
backend/            Django settings and URLs
api/                REST API: models, views, services (AI, coaching rules, insights)
app/                React frontend (pages: Dashboard, MealLogger, DietPlan, Workouts, Profile)
scripts/            seed_demo_data.py: creates demo users with meals and plans
docs/API_ENDPOINTS.md   endpoint reference
```

## Run it locally

```bash
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver          # API at http://127.0.0.1:8000/api/v1
```

```bash
cd app
npm install
npm run dev                         # http://localhost:5173
```

## Note on the AI features

The Gemini keys in `api/services/ai_service.py` are left empty, so photo scanning and the chatbot return default answers. To try them, put your own key in `API_KEY_1` (and don't commit it).

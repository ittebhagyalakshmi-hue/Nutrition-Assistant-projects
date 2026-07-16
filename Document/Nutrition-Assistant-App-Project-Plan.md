# Nutrition Assistant App — Project Plan
### College Major Project | MERN Stack

---

## 1. Project Overview

The **Nutrition Assistant App** is a full-stack web application built on the MERN stack (MongoDB, Express.js, React.js, Node.js) that helps users track their daily food intake, monitor nutritional values (calories, protein, carbs, fats, etc.), set personalized health goals, and receive diet recommendations.

The system allows users to log meals, search a food database, visualize their nutrition trends through charts, and get insights into whether they're meeting their daily targets (weight loss, weight gain, maintenance, muscle building, etc.). An admin panel manages the food database and monitors platform usage.

This project demonstrates full-stack development skills: RESTful API design, authentication, database modeling, state management, data visualization, and responsive UI design — making it suitable as a college major/capstone project.

---

## 2. Objectives

- Build a secure, role-based (User/Admin) web application using the MERN stack.
- Allow users to register, log in, and manage their health profile (age, weight, height, activity level, goals).
- Provide a searchable food/nutrition database (calories, macros, micros).
- Enable users to log daily meals and automatically calculate consumed nutrition.
- Calculate personalized daily calorie/macro targets (using BMR/TDEE formulas).
- Visualize nutrition intake trends via charts/dashboards.
- Allow admins to manage (CRUD) the food database and view platform statistics.
- Implement authentication & authorization using JWT.
- Ensure the application is responsive and works across devices.
- Follow industry-standard project architecture and coding practices suitable for academic evaluation and future scalability.

---

## 3. Features List

**User Features**
- User registration/login (JWT-based authentication)
- Profile setup (age, gender, height, weight, activity level, goal)
- BMR/TDEE-based daily calorie & macro target calculation
- Food search (from database) with nutrition info
- Add/log meals (breakfast, lunch, dinner, snacks) with quantity
- Daily/weekly nutrition summary (calories, protein, carbs, fat)
- Progress dashboard with charts (daily intake vs. target)
- Water intake tracker (optional add-on)
- Weight tracking log with progress graph
- Edit/delete logged meals
- Set and update health goals

**Admin Features**
- Admin login (separate role)
- Add/edit/delete food items in the database
- View registered users
- View platform usage statistics
- Manage reported/incorrect food entries

**General**
- Responsive UI (mobile/tablet/desktop)
- Search and filter functionality
- Notifications/alerts (e.g., "You're under your protein goal today")

---

## 4. Functional Requirements

| ID | Requirement |
|----|-------------|
| FR1 | System shall allow users to register and log in securely |
| FR2 | System shall allow users to create/update a health profile |
| FR3 | System shall calculate daily calorie & macro targets based on profile data |
| FR4 | System shall allow users to search food items from the database |
| FR5 | System shall allow users to log meals with date, time, and quantity |
| FR6 | System shall calculate total nutrition consumed per day automatically |
| FR7 | System shall display nutrition data via charts/graphs |
| FR8 | System shall allow users to track weight over time |
| FR9 | System shall allow admins to perform CRUD operations on food data |
| FR10 | System shall restrict admin routes to authorized admin users only |
| FR11 | System shall allow users to edit/delete their logged meals |
| FR12 | System shall persist all data in MongoDB via REST APIs |

---

## 5. Non-Functional Requirements

| ID | Requirement |
|----|-------------|
| NFR1 | **Security** — Passwords hashed (bcrypt), JWT-based route protection |
| NFR2 | **Performance** — API responses under 300ms for standard queries |
| NFR3 | **Scalability** — Modular backend structure to support future features |
| NFR4 | **Usability** — Clean, intuitive, responsive UI (mobile-first) |
| NFR5 | **Reliability** — Proper error handling & validation on client and server |
| NFR6 | **Maintainability** — Well-structured, documented, reusable code |
| NFR7 | **Availability** — Deployable on cloud platforms (Render/Vercel/Netlify/Atlas) |
| NFR8 | **Data Integrity** — Input validation using libraries like Joi/express-validator |

---

## 6. Technology Stack

**Frontend**
- React.js (with Vite or CRA)
- React Router DOM
- Redux Toolkit / Context API (state management)
- Axios (API calls)
- Chart.js or Recharts (data visualization)
- Tailwind CSS / Material UI / Bootstrap (styling)

**Backend**
- Node.js
- Express.js
- JWT (jsonwebtoken) for authentication
- bcrypt.js for password hashing
- express-validator / Joi for validation
- Multer (if profile pictures/food images are needed)

**Database**
- MongoDB (MongoDB Atlas for cloud hosting)
- Mongoose (ODM)

**Dev Tools & Others**
- Postman (API testing)
- Git & GitHub (version control)
- dotenv (environment variables)
- nodemon (dev server auto-restart)
- Concurrently (run client & server together in dev)

**Deployment**
- Frontend: Vercel / Netlify
- Backend: Render / Railway
- Database: MongoDB Atlas

---

## 7. Complete MERN Folder Structure

```
nutrition-assistant-app/
│
├── client/                          # React Frontend
│   ├── public/
│   │   └── index.html
│   │
│   ├── src/
│   │   ├── assets/                  # Images, icons, logos
│   │   ├── components/              # Reusable UI components
│   │   │   ├── common/               # Navbar, Footer, Loader, Modal, ProtectedRoute
│   │   │   ├── charts/               # NutritionChart, WeightChart
│   │   │   ├── food/                 # FoodCard, FoodSearchBar
│   │   │   └── meal/                 # MealLogItem, MealForm
│   │   │
│   │   ├── pages/                   # Route-level pages
│   │   │   ├── Auth/                 # Login.jsx, Register.jsx
│   │   │   ├── Dashboard/            # Dashboard.jsx
│   │   │   ├── Profile/              # ProfileSetup.jsx, ProfileEdit.jsx
│   │   │   ├── Meals/                # MealLog.jsx, MealHistory.jsx
│   │   │   ├── Admin/                # AdminDashboard.jsx, ManageFood.jsx
│   │   │   └── NotFound.jsx
│   │   │
│   │   ├── redux/ (or context/)     # State management
│   │   │   ├── slices/               # authSlice.js, userSlice.js, mealSlice.js
│   │   │   └── store.js
│   │   │
│   │   ├── services/                # Axios API call functions
│   │   │   ├── authService.js
│   │   │   ├── foodService.js
│   │   │   ├── mealService.js
│   │   │   └── userService.js
│   │   │
│   │   ├── utils/                   # Helper functions (BMR calc, formatters)
│   │   ├── hooks/                   # Custom React hooks
│   │   ├── routes/                  # AppRoutes.jsx, PrivateRoute.jsx
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   │
│   ├── .env
│   ├── package.json
│   └── vite.config.js
│
├── server/                          # Node/Express Backend
│   ├── config/
│   │   ├── db.js                    # MongoDB connection
│   │   └── config.js                # General config/env loader
│   │
│   ├── models/                      # Mongoose schemas
│   │   ├── User.js
│   │   ├── Food.js
│   │   ├── Meal.js
│   │   └── WeightLog.js
│   │
│   ├── controllers/                 # Business logic
│   │   ├── authController.js
│   │   ├── userController.js
│   │   ├── foodController.js
│   │   ├── mealController.js
│   │   └── adminController.js
│   │
│   ├── routes/                      # API routes
│   │   ├── authRoutes.js
│   │   ├── userRoutes.js
│   │   ├── foodRoutes.js
│   │   ├── mealRoutes.js
│   │   └── adminRoutes.js
│   │
│   ├── middleware/
│   │   ├── authMiddleware.js        # JWT verification
│   │   ├── adminMiddleware.js       # Admin role check
│   │   ├── errorMiddleware.js       # Centralized error handling
│   │   └── validateMiddleware.js    # Request validation
│   │
│   ├── utils/
│   │   ├── generateToken.js
│   │   └── calorieCalculator.js     # BMR/TDEE formulas
│   │
│   ├── .env
│   ├── server.js                    # Entry point
│   └── package.json
│
├── .gitignore
├── README.md
└── package.json                     # Root (concurrently scripts)
```

---

## 8. Explanation of Each Folder and File

### Frontend (`client/`)
- **public/index.html** — Root HTML file where React mounts.
- **src/assets/** — Static images, icons, and logos used across the UI.
- **src/components/common/** — Shared components like Navbar, Footer, Loader, and route guards used across multiple pages.
- **src/components/charts/** — Chart components (built with Chart.js/Recharts) to visualize nutrition and weight trends.
- **src/components/food/** — Components related to displaying and searching food items.
- **src/components/meal/** — Components for logging and displaying meals.
- **src/pages/** — Full page views mapped to routes (Login, Register, Dashboard, Profile, Meal Log, Admin panel).
- **src/redux/** — Global state management: auth state, user profile state, meal/food state (Redux Toolkit slices + store).
- **src/services/** — Centralized Axios functions that call backend API endpoints (keeps API logic out of components).
- **src/utils/** — Helper functions (e.g., BMR calculation on the client side, date formatting).
- **src/hooks/** — Custom hooks (e.g., `useAuth`, `useFetch`).
- **src/routes/** — Route definitions, including protected/private routes for authenticated users and admins.
- **App.jsx / main.jsx** — Root component and React DOM entry point.
- **.env** — Frontend environment variables (e.g., API base URL).

### Backend (`server/`)
- **config/db.js** — Establishes MongoDB connection using Mongoose.
- **config/config.js** — Centralizes environment variable access.
- **models/** — Mongoose schemas defining data structure:
  - `User.js` — user credentials, profile info, goals.
  - `Food.js` — food item name, calories, macros per serving.
  - `Meal.js` — logged meals linked to a user and food items.
  - `WeightLog.js` — user's weight history over time.
- **controllers/** — Contains logic for handling requests (e.g., register user, calculate nutrition, CRUD food items).
- **routes/** — Defines API endpoints and maps them to controller functions.
- **middleware/authMiddleware.js** — Verifies JWT tokens to protect private routes.
- **middleware/adminMiddleware.js** — Ensures only admin users can access admin-only routes.
- **middleware/errorMiddleware.js** — Catches and formats errors consistently across the API.
- **middleware/validateMiddleware.js** — Validates incoming request bodies (e.g., using express-validator).
- **utils/generateToken.js** — Generates JWT tokens on login/register.
- **utils/calorieCalculator.js** — Contains BMR/TDEE formula logic for calculating personalized nutrition targets.
- **server.js** — Main entry point; initializes Express app, connects middleware, routes, and DB.
- **.env** — Backend environment variables (DB URI, JWT secret, port).

### Root
- **.gitignore** — Excludes node_modules, .env, build files from Git.
- **README.md** — Project documentation.
- **package.json (root)** — Optional scripts to run client & server concurrently during development.

---

## 9. Required NPM Packages

### Frontend (`client`)
```
react
react-dom
react-router-dom
axios
@reduxjs/toolkit
react-redux
chart.js
react-chartjs-2        (or recharts)
tailwindcss            (or @mui/material + @emotion/react @emotion/styled)
react-icons
react-hook-form        (form handling & validation)
react-toastify         (notifications/alerts)
```

### Backend (`server`)
```
express
mongoose
dotenv
bcryptjs
jsonwebtoken
cors
express-validator      (or joi)
morgan                 (request logging)
helmet                 (security headers)
multer                 (file/image uploads, optional)
```

### Dev Dependencies
```
nodemon         (backend auto-restart)
concurrently    (run client + server together)
vite            (frontend build tool, if using Vite instead of CRA)
```

---

## 10. How the Application Will Work

1. **User Onboarding**
   A new user registers with email/password (hashed via bcrypt). Upon login, the server issues a JWT stored on the client (in memory/cookie), used to authenticate future requests.

2. **Profile Setup**
   The user fills in age, gender, height, weight, activity level, and goal (lose/gain/maintain weight). The backend uses this data with BMR/TDEE formulas (`calorieCalculator.js`) to compute a personalized daily calorie and macro target, stored in the user's profile.

3. **Food Database & Search**
   The `Food` collection stores nutrition data for common food items (seeded by admin or imported from a public nutrition dataset/API). Users search this database via the food search bar, which queries the `/api/food` endpoint.

4. **Meal Logging**
   When a user logs a meal (e.g., "2 eggs" for breakfast), the frontend sends the food ID, quantity, and meal type to `/api/meals`. The backend calculates the nutritional contribution and saves it as a `Meal` document linked to the user and date.

5. **Dashboard & Visualization**
   The dashboard fetches the day's/week's logged meals, aggregates total calories/macros consumed, and compares them against the user's daily targets. This is visualized using bar/line/pie charts (Chart.js/Recharts), showing progress toward goals.

6. **Weight Tracking**
   Users can periodically log their weight; this is stored in `WeightLog` and rendered as a trend line graph to show progress over time.

7. **Admin Panel**
   Admins log in with elevated privileges (role field in `User` model). They can add/edit/delete food items in the database and view overall platform statistics (total users, most logged foods, etc.), protected by `adminMiddleware`.

8. **Authentication Flow**
   Every protected route (frontend and backend) checks for a valid JWT. `authMiddleware` verifies tokens server-side; `PrivateRoute`/`ProtectedRoute` components guard frontend routes, redirecting unauthenticated users to login.

9. **Data Flow Summary**
   React (client) → Axios API calls → Express routes → Controllers → Mongoose models → MongoDB Atlas → Response back to client → Redux store updates → UI re-renders with fresh data.

10. **Deployment**
    The React frontend is built and deployed to Vercel/Netlify; the Express backend is deployed to Render/Railway; MongoDB Atlas serves as the cloud database — connected via environment variables for a fully functional production deployment.

---

**Status:** Planning phase complete. Awaiting next instructions before writing any code.

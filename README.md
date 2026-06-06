# 🍎 RescueMeal - AI-Assisted Food Donation Platform

RescueMeal is a full-stack MERN (MongoDB, Express.js, React.js, Node.js) application designed to bridge the gap between food waste and hunger. It connects food donors (restaurants, supermarkets, individuals) with NGOs and people in need.

This project is built as a **placement showpiece**, featuring a simulated **AI Expiry Predictor engine**, **Light/Dark theme toggling**, and **role-based access control (RBAC)**.

---

## 💡 Key Features

### 1. 🧠 AI Food Expiry Predictor (Interview Showpiece)
* **Keyword NLP Classification**: Scans food titles (using regular expressions) to categorize listings into specific food safety profiles (`Rice`, `Biryani`, `Curry`, `Snacks`, or `Generic`).
* **Environmental Expiry Mapping**: Evaluates optimal shelf-life thresholds against FDA food safety standards depending on the chosen `storageMethod` (Room Temperature, Refrigerated, Frozen).
* **Mongoose Virtual Getters**: Computes `currentRemainingHours` and `currentRiskLevel` dynamically in real-time based on the database clock whenever a listing is fetched.
* **Live Prediction Playground**: Gives donors a real-time preview of the AI classification, confidence score, shelf-life, and safety risk *before* posting.
* **Safety progress bar**: Renders dynamic, color-coded progress meters (Green ➔ Yellow ➔ Red) on food cards to track remaining safety hours.

### 2. 👥 Role-Based Workflows
* **Donors**:
  * Post surplus food listings with description, quantity, cooked time, storage, and image uploads.
  * Real-time AI prediction preview.
  * Manage incoming claims (Approve/Reject requests).
  * Direct handover/delivery confirmation.
* **NGOs (Food Transport Partners)**:
  * Browse community surplus food listings.
  * Accept and claim food directly.
  * Manage pickups on a dedicated "My Deliveries" board.
  * Confirm delivery once food is distributed.
* **Needy Persons**:
  * Browse available food offerings.
  * Submit food aid requests in one click.
  * Track request approval status in real-time.

### 3. 🌗 Dual Light & Dark Theme
* Implements a state-retaining Light & Dark theme toggle using CSS variables and Tailwind class-based configurations.
* Stores user theme preferences in `localStorage` for session persistence.

---

## 🛠️ Tech Stack

* **Frontend**: React.js (Vite), Tailwind CSS, Lucide Icons, Axios, React Router Dom
* **Backend**: Node.js, Express.js, JWT Authentication, Multer (Local static serving)
* **Database**: MongoDB (Mongoose Schemas, hooks, and virtual properties)
* **Cloud Uploads**: Cloudinary integration with local disk fallback

---

## 📂 Project Structure

```
rescuemeal/
├── backend/
│   ├── config/             # DB & Cloudinary configuration
│   ├── controllers/        # Express controllers (auth, donation, request)
│   ├── middleware/         # Auth, file upload & role validation middlewares
│   ├── models/             # Mongoose schemas (User, Donation, Request)
│   ├── routes/             # Express routes
│   ├── uploads/            # Local fallback storage folder
│   ├── server.js           # Server entry point
│   └── vercel.json         # Vercel deployment configuration
└── frontend/
    ├── src/
    │   ├── components/     # Reusable components (Navbar, DonationCard, PrivateRoute)
    │   ├── context/        # Global Auth Context
    │   ├── pages/          # Home, Login, Register, Dashboards, Available Food, Deliveries
    │   ├── utils/          # Axios custom client instance
    │   └── App.jsx         # App routes
    ├── tailwind.config.js  # Tailwind theme settings
    └── index.html          # SEO metadata
```

---

## ⚙️ Local Setup and Installation

### Prerequisites
* [Node.js](https://nodejs.org/) installed
* [MongoDB](https://www.mongodb.com/) running locally on port `27017`

### 1. Backend Setup
1. Navigate to the backend directory:
   ```bash
   cd backend
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Create a `.env` file in the `backend/` directory:
   ```env
   PORT=5000
   MONGODB_URI=mongodb://localhost:27017/rescuemeal
   JWT_SECRET=supersecretrescuemealjwtkey123!
   ```
4. Start the server:
   ```bash
   npm start
   ```
   *(Backend will start on `http://localhost:5000`)*

### 2. Frontend Setup
1. Open a new terminal and navigate to the frontend directory:
   ```bash
   cd frontend
   ```
2. Install dependencies:
   ```bash
   npm install --legacy-peer-deps
   ```
3. Start the dev server:
   ```bash
   npm run dev
   ```
   *(Frontend will start on `http://localhost:5173`)*

---

## ☁️ Deployment (Vercel serverless)

This project is pre-configured for Vercel:
* **Backend**: Deploy the `backend` subdirectory. Set environment variables `MONGODB_URI` (MongoDB Atlas cluster link) and `JWT_SECRET`.
* **Frontend**: Deploy the `frontend` subdirectory. Set the environment variable `VITE_API_URL` pointing to your deployed backend (e.g. `https://rescuemeal-backend.vercel.app/api`).
* Refer to the `deployment_guide.md` file in the root folder for step-by-step screenshots and guidelines.

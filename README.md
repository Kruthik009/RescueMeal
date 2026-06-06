# RescueMeal - AI-Assisted Food Donation Platform

RescueMeal is a food donation platform built using the MERN stack that connects food donors (restaurants, supermarkets, individuals) with NGOs and people in need.

### 🔗 Live Demo: [https://rescuemeal-frontend.vercel.app](https://rescuemeal-frontend.vercel.app)

---

## 🛠️ Tech Stack
* **Frontend**: React.js (Vite), Tailwind CSS
* **Backend**: Node.js, Express.js, JWT Authentication
* **Database**: MongoDB (Mongoose)

---

## 💡 Key Features
* **AI Expiry Predictor**: Classifies food types (Biryani, Curry, Rice, Snacks) and automatically calculates dynamic remaining safe hours based on the storage method.
* **Donor Dashboard**: List surplus food, preview safety predictions, and approve request claims.
* **NGO Dashboard**: Browse community listings, claim food, and track deliveries.
* **Needy Person Dashboard**: Browse food and request aid in one click.
* **Dual Theme**: Toggle between Light and Dark mode.

---

## ⚙️ How to Run Locally

### 1. Start MongoDB
Make sure MongoDB is running locally on port `27017`.

### 2. Run Backend
```bash
cd backend
npm install
# Add PORT=5000, MONGODB_URI=mongodb://localhost:27017/rescuemeal, JWT_SECRET=secret to .env file
npm start
```

### 3. Run Frontend
```bash
cd frontend
npm install --legacy-peer-deps
npm run dev
```

Open **`http://localhost:5173`** in your browser.

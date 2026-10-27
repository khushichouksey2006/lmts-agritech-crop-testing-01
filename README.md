# 🌾 AgriTech — Unified Smart Agriculture & Precision Farming Platform

AgriTech is a full-stack, enterprise-grade agricultural management web application engineered for modern farmers, agronomists, and agri-input suppliers. It integrates farm land parcel telemetry, crop lifecycle tracking, agro-meteorological forecasting, certified input procurement, and role-protected administrative governance.

---

## 🌟 Key Application Modules & Features

### 1. 🚜 Smart Farm Parcel Telemetry
- Register and manage distinct land holdings and plots.
- Record acreage in hectares, soil types (Loamy, Clay Loam, Black Cotton, Sandy Loam), and irrigation infrastructure (Canal Drip, Solar Tube-well, Rainfed).
- Safe cascading deletion: Removing a farm plot automatically cleans up its associated plantings.

### 2. 🌱 Precision Crop Growth Tracking
- Associate planted crops with registered farm plots.
- Record sowing dates, estimated harvest windows, and planted acreage.
- Real-time growth status tracking (`Planted`, `Germinated`, `Vegetative`, `Flowering`, `Maturing`, `Harvested`).
- Custom agronomic notes for fertilizer application and soil health.

### 3. 📖 Agronomic Knowledge & Cultivation Library
- Curated agronomy protocols for staple cereals, vegetables, cash crops, and legumes (Wheat, Rice, Maize, Tomato, Cotton, Soybean).
- Sowing and harvest calendar windows, optimal temperature ranges, rainfall needs, and soil compatibility.
- Step-by-step accordion lifecycle stages from germination to ripening.
- Integrated Pest Management (IPM) guidelines and irrigation strategies.

### 4. 🛒 Certified Agri-Marketplace & Orders
- Browse certified hybrid seeds, slow-release bio-fertilizers, organic pesticides, and solar drip irrigation controllers.
- Multi-category filtering and instant keyword search.
- **Server-Side Price Validation**: To prevent price tampering, order subtotals and totals are computed strictly on the backend from authoritative catalog data.
- Inventory stock decrement and availability tracking.
- Order history with tracking statuses (`Processing`, `Shipped`, `Delivered`, `Cancelled`).

### 5. ⛅ Agro-Meteorology Weather Station
- Query atmospheric conditions by city name or GPS geolocation (`navigator.geolocation`).
- Key metrics: Temperature (°C), Humidity (%), Wind Speed (m/s), and Atmospheric Pressure (hPa).
- Dynamic operational farming advisories (e.g., spraying windows, fungal pathogen alerts).
- Secure backend proxying keeping API keys confidential on the server.
- Built-in simulation fallback when no external API key is configured.

### 6. 🛡️ Role-Protected Administration
- Granular role-based access control (RBAC) powered by JSON Web Tokens (JWT).
- Admin command center with real-time KPI metrics (Total Users, Catalog Products, Orders, Gross Revenue, Database Engine mode).
- User management: List all platform users and promote/demote roles.
- Product inventory management: Add, edit, adjust prices/stock, and remove products.
- Order fulfillment: Update shipment statuses (`Pending` &rarr; `Processing` &rarr; `Shipped` &rarr; `Delivered`).

### 7. 🔌 Dual-Engine Database Architecture
- **Persistent Mode**: Automatic connection to MongoDB with Mongoose schemas and relationships.
- **Demo In-Memory Mode**: If MongoDB is not running locally or in Atlas, the server automatically transitions to an In-Memory data store pre-populated with realistic demo data, clearly labeled in the UI.

---

## 🚀 Quick Start Guide

### Prerequisites
- Node.js (v18 or higher recommended)
- npm (v9 or higher)

### 1. Backend Setup & Startup

```bash
cd AgriTech/Server

# Configuration (already populated with dev defaults)
cp .env.example .env

# Start Server
npm start
# or for auto-reload during development:
npm run dev
```

- Backend Server URL: `http://localhost:5000`
- API Health Status: `http://localhost:5000/api/health`

### 2. Frontend Setup & Startup

```bash
cd AgriTech/Client

# Start Development Server
npm run dev
```

- Application URL: `http://localhost:5173`

---

## 🔑 Demo Accounts (Pre-configured)

For quick review and demonstration, one-click demo login buttons are provided on the login page:

| Role | Email | Password | Access Capabilities |
| :--- | :--- | :--- | :--- |
| **Farmer (User)** | `farmer@agritech.com` | `password123` | Farms, Crops, Orders, Weather, Marketplace |
| **Platform Admin** | `admin@agritech.com` | `password123` | Full Admin Console, Products CRUD, Users Management, Order Logistics |

*You can also register a brand-new farmer account at `/register`.*

---

## ⚙️ Environment Variables

### Server Configuration (`AgriTech/Server/.env`)

| Variable | Description | Default / Example |
| :--- | :--- | :--- |
| `PORT` | Backend port | `5000` |
| `JWT_SECRET` | Secret key for signing authentication tokens | `agritech_jwt_secret_dev_key_agri_2026_safe` |
| `JWT_EXPIRES_IN` | Token validity duration | `7d` |
| `MONGODB_URI` | MongoDB connection string (Optional) | `mongodb://127.0.0.1:27017/agritech` |
| `OPENWEATHER_API_KEY`| OpenWeatherMap API key (Optional) | *(Empty: uses simulated agro-weather)* |
| `CLIENT_URL` | Permitted origin for CORS | `http://localhost:5173` |

---

## 🛠️ Tech Stack

- **Frontend**: React 18, Vite, React Router DOM 6, Axios, Bootstrap 5, React-Bootstrap, React Icons.
- **Backend**: Node.js, Express, Mongoose / In-Memory Store, JWT (`jsonwebtoken`), `bcryptjs`, `dotenv`, `cors`, `axios`.
- **Styling**: Modern agricultural green-and-white theme (`Plus Jakarta Sans` typography, accessible contrast, custom CSS components).

## 📄 Purpose

This project is built for **learning and practice purposes** as part of a personal development journey to understand full-stack web development concepts including:

- Building REST APIs with ASP.NET Core
- Managing databases with Entity Framework Core
- Implementing authentication & authorization with ASP.NET Identity
- Integrating third-party services (Cloudinary, Stripe)
- Building interactive UIs with React, TypeScript, and Redux
- Connecting frontend and backend in a real-world application structure

> This is not intended for production use.
---

## 🧰 Tech Stack

### Backend
- **.NET 9** — ASP.NET Core Web API
- **Entity Framework Core** — ORM with SQLite (local) or SQL Server
- **ASP.NET Core Identity** — Authentication & role-based authorization
- **Cloudinary** — Product image upload & management
- **Stripe** — Payment processing
- **AutoMapper** — Object mapping
- **Swagger / OpenAPI** — API documentation

### Frontend
- **React 19** + **TypeScript**
- **Redux Toolkit + RTK Query** — State management & API calls
- **Material UI (MUI)** — Component library
- **React Router** — Client-side routing
- **Stripe.js** — Payment UI

---

## 📂 Project Structure

```
E-Commerce_v1/
├── API/                  # ASP.NET Core Web API
│   ├── Controllers/      # API endpoints
│   ├── Data/             # DbContext, migrations, seeder
│   ├── Entities/         # Domain models
│   ├── Services/         # Cloudinary, Stripe, Discount services
│   ├── Middleware/       # Global error handling
│   └── appsettings.json  # App configuration
├── client/               # React + TypeScript frontend
│   ├── src/
│   │   ├── app/          # Store, API, layout, routes
│   │   └── features/     # Catalog, cart, orders, admin
│   └── .env              # Frontend environment variables
├── .gitignore
├── README.md
└── Restore.sln
```

---

## ⚙️ Prerequisites

- [.NET 9 SDK](https://dotnet.microsoft.com/download/dotnet/9.0)
- [Node.js](https://nodejs.org/) (v18+)
- [dotnet-ef CLI tools](https://learn.microsoft.com/en-us/ef/core/cli/dotnet)

```bash
dotnet tool install --global dotnet-ef
```

---

## 🚀 Local Setup

### 1. Clone the repository

```bash
git clone https://github.com/riri97-igm/E-Commerce_v1.git
cd E-Commerce_v1
```

### 2. Configure the backend

Create `API/appsettings.Development.json` based on the template below:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "ConnectionStrings": {
    "DefaultConnection": "Data Source=store.db"
  },
  "Cloudinary": {
    "CloudName": "your_cloud_name",
    "ApiKey": "your_api_key",
    "ApiSecret": "your_api_secret"
  },
  "StripeSettings": {
    "PublishableKey": "your_stripe_publishable_key",
    "SecretKey": "your_stripe_secret_key",
    "WhSecret": "your_stripe_webhook_secret"
  }
}
```

> ⚠️ This file is in `.gitignore` — never commit it with real credentials.

### 3. Run database migrations

```bash
cd API
dotnet ef database update
```

This will auto-create the `store.db` SQLite database and seed it with sample products and users.

### 4. Run the backend

```bash
cd API
dotnet run
```

API runs at: `https://localhost:5001`  
Swagger UI: `https://localhost:5001/swagger`

> First time setup — trust the dev certificate:
> ```bash
> dotnet dev-certs https --trust
> ```

### 5. Configure the frontend

Create `client/.env`:

```env
VITE_API_URL=https://localhost:5001/api/
VITE_STRIPE_PK=your_stripe_publishable_key
```

### 6. Run the frontend

```bash
cd client
npm install --legacy-peer-deps
npm start
```

Frontend runs at: `https://localhost:3000`

---

## 🔐 Default Seeded Users

| Role  | Username | Password   |
|-------|----------|------------|
| Admin | admin    | Pa$$w0rd   |
| User  | bob      | Pa$$w0rd   |

---

## 🌐 External Services

| Service | Purpose | Free Tier |
|---------|---------|-----------|
| [Cloudinary](https://cloudinary.com) | Product image upload | ✅ Yes |
| [Stripe](https://stripe.com) | Payment processing | ✅ Test mode |

---

## 📝 Notes

- SQLite is used for local development — no database server installation needed.
- Cloudinary is only required for admin product image upload. The app runs fine without it for browsing, cart, and checkout.
- Stripe test mode works with test card number `4242 4242 4242 4242`.

---

## 📄 License

This project is for educational purposes.

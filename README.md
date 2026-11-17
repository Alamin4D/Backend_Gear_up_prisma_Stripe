
# GrabGear 🏕️🚴‍♂️

**A RESTful Backend API for Sports & Outdoor Equipment Rental**

GrabGear is a full-stack equipment rental marketplace backend that connects customers with equipment providers across Bangladesh. It enables customers to rent sports and outdoor gear, make secure payments, and manage rental orders, while providers manage their inventory and administrators oversee platform activities.

## 🚀 Live API & Documentation

- **Live API:** https://backend-gear-up-prisma-stripe.vercel.app/api/v1
- **Swagger Documentation:** https://backend-gear-up-prisma-stripe.vercel.app/api-docs
- **Frontend Repository:** https://github.com/Alamin4D/Frontend_Gear_up_prisma_Stripe

## 🛠️ Tech Stack

| Category | Technology |
|---|---|
| Runtime | Node.js |
| Framework | Express.js |
| Language | TypeScript |
| Database | PostgreSQL (NeonDB) |
| ORM | Prisma Client |
| Authentication | JWT & bcryptjs |
| Validation | Zod |
| Payment Gateway | Stripe |
| API Documentation | Swagger |
| Deployment | Vercel |

## ✨ Key Features

### 👤 Role-Based Access Control (RBAC)

**Customer**
- Browse and search available equipment.
- Place rental orders.
- Make payments through Stripe.
- View rental orders and payment history.
- Submit equipment reviews.

**Provider**
- Create, update, and delete equipment listings.
- Manage equipment inventory.
- View incoming rental orders.
- Update order statuses, including `PICKED_UP` and `RETURNED`.

**Admin**
- Manage equipment categories.
- View platform users.
- Oversee platform activities.

### 🔐 Authentication & Security

- JWT-based authentication.
- Password hashing with bcryptjs.
- Role-based authorization.
- Request validation using Zod.
- Centralized error handling for application, Prisma, and validation errors.

### 💳 Payment Integration

- Stripe Checkout integration.
- Payment session creation.
- Payment verification.
- Database transactions to synchronize payment records and order status.

### 🗄️ Database Management

- PostgreSQL database hosted on NeonDB.
- Prisma ORM for database queries.
- Transaction-based data consistency.
- Seed data for testing different user roles.

### 📚 API Documentation

- Swagger documentation using `swagger-jsdoc` and `swagger-ui-express`.
- Interactive API testing through Swagger UI.
- Documented request parameters, responses, and endpoints.

## ⚙️ Getting Started

### Prerequisites

- Node.js v18 or later
- npm
- PostgreSQL database or NeonDB account
- Stripe developer account

### 1. Clone the Repository

```bash
git clone https://github.com/m-d-Irfan/Backend_Gear_up_prisma_Stripe.git
cd Backend_Gear_up_prisma_Stripe
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Create a `.env` file in the project root and configure the following variables.

```env
NODE_ENV=development
PORT=5000

DATABASE_URL="postgresql://username:password@localhost:5432/gearup_db"

JWT_ACCESS_SECRET="your_jwt_secret"
JWT_ACCESS_EXPIRES_IN="7d"

STRIPE_SECRET_KEY="sk_test_your_key"
```

Replace the placeholder values with your actual development credentials.

**Important:** Never commit your `.env` file or expose your Stripe secret key in public repositories.

### 4. Initialize the Database

Run the following command to synchronize the Prisma schema with your database.

```bash
npx prisma db push
```

### 5. Seed the Database

```bash
npm run seed
```

The seed script creates demo users and sample equipment for testing, according to the project's seed configuration.

### 6. Start the Development Server

```bash
npm run dev
```

The API should be available at:

- **API Base URL:** http://localhost:5000/api/v1
- **Swagger UI:** http://localhost:5000/api-docs

## 🔑 Demo Credentials

The following seeded accounts are provided for testing:

| Role | Email | Password |
|---|---|---|
| Admin | `admin@gearup.com` | `Admin123!` |
| Provider | `provider@gearup.com` | `Provider123!` |
| Customer | `customer@gearup.com` | `Customer123!` |

Use these credentials only with the appropriate development or demo environment.

## 🔗 API Endpoints

| Module | Method | Endpoint | Access |
|---|---|---|---|
| Authentication | POST | `/api/v1/auth/register` | Public |
| Authentication | POST | `/api/v1/auth/login` | Public |
| Equipment | GET | `/api/v1/gear` | Public |
| Equipment | POST | `/api/v1/gear` | Provider/Admin |
| Orders | POST | `/api/v1/orders` | Customer |
| Orders | PATCH | `/api/v1/orders/:id/status` | Provider/Admin |
| Payments | POST | `/api/v1/payments/create-checkout-session` | Customer |
| Payments | POST | `/api/v1/payments/verify` | Customer |

For complete endpoint details, request schemas, and responses, visit the [Swagger Documentation](https://backend-gear-up-prisma-stripe.vercel.app/api-docs).

## 🧪 Testing with Swagger UI

1. Open the [Swagger UI](https://backend-gear-up-prisma-stripe.vercel.app/api-docs).
2. Execute `POST /api/v1/auth/login` with a demo account.
3. Copy the returned access token.
4. Click the **Authorize** button.
5. Enter `Bearer YOUR_ACCESS_TOKEN`.
6. Click **Authorize** and close the dialog.
7. Test the endpoints available to your account's role.

## 📁 Project Structure

```text
Backend_Gear_up_prisma_Stripe/
├── prisma/
│   └── schema.prisma
├── src/
│   ├── app.ts
│   ├── server.ts
│   ├── routes/
│   ├── controllers/
│   ├── services/
│   ├── middlewares/
│   ├── utils/
│   └── ...
├── .env.example
├── package.json
├── tsconfig.json
└── README.md
```

*Note: The folder structure above is illustrative. Adjust it to match the actual repository.*

## 🚀 Deployment

The backend is deployed on Vercel and uses PostgreSQL hosted on NeonDB.

Before deploying, configure the required environment variables in your hosting dashboard, including the database connection string, JWT secret, and Stripe secret key.

## 📄 License

This project is available under the MIT License.

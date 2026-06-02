# FoodFleet Full Stack Project

This ZIP contains your original React frontend plus a complete Node.js/Express backend connected to Microsoft SQL Server / SQL Server Management Studio.

## Included

- `frontend/` - React frontend
- `backend/` - Express REST API + Socket.IO backend
- `database/schema.sql` - SQL Server database and table creation script
- `database/seed.sql` - Demo users, restaurants, riders, menu items and notifications
- Root `package.json` - convenience scripts for installing/running both apps

## Backend Features

The backend implements the API routes already used by your frontend:

- Authentication: register, login, current user
- Customer: restaurants, restaurant details, orders, reviews, favorites
- Restaurant: profile, categories, menu management, orders, statistics
- Rider: profile, availability, active orders, history, pickup/delivery confirmation
- Admin: users, orders, rider assignment, analytics
- Notifications with Socket.IO real-time events

## Requirements

Install these first:

- Node.js 18 or newer
- Microsoft SQL Server
- SQL Server Management Studio, Azure Data Studio, or sqlcmd

## Database Setup in SSMS

1. Open SQL Server Management Studio.
2. Connect to your SQL Server instance.
3. Open and run `database/schema.sql`.
4. Open and run `database/seed.sql`.

Demo login accounts are:

| Role | Email | Password |
| --- | --- | --- |
| Admin | admin@foodfleet.com | password123 |
| Customer | customer@foodfleet.com | password123 |
| Restaurant | restaurant@foodfleet.com | password123 |
| Rider | rider@foodfleet.com | password123 |

## Backend Setup

From the project root:

```bash
cd backend
copy .env.example .env
npm install
npm run dev
```

Edit `backend/.env` to match your SQL Server settings:

```env
DB_USER=sa
DB_PASSWORD=YourStrongPassword123
DB_SERVER=localhost
DB_DATABASE=FoodFleetDB
DB_PORT=1433
DB_ENCRYPT=false
DB_TRUST_SERVER_CERTIFICATE=true
```

The backend runs at:

```text
http://localhost:5000
http://localhost:5000/api
```

## Frontend Setup

Open a second terminal:

```bash
cd frontend
copy .env.example .env
npm install
npm start
```

The frontend runs at:

```text
http://localhost:3000
```

## Install Everything From Root

You can also install both frontend and backend dependencies from the root folder:

```bash
npm install
npm run install:all
npm run dev
```

## Important Notes

If SQL Server uses Windows Authentication instead of SQL username/password, create a SQL login for this project or adjust the `mssql` connection code in `backend/src/config/db.js`.

If your SQL Server instance is named, for example `localhost\SQLEXPRESS`, use that value for `DB_SERVER` and keep `DB_PORT` only if your instance accepts TCP connections on that port.

For production, change `JWT_SECRET` in `backend/.env` to a long random secret.

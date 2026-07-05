# Helpdesk Application

A modern, full-stack helpdesk application built with React and Node.js, inspired by Zoho Desk.

## 🚀 Live Demo
👉 [**Helpdesk Application on Vercel**](https://helpdesk-deployed.vercel.app/)

## Features

- **Role-Based Access Control**: SUPER_ADMIN, ADMIN, AGENT, MANAGER, CUSTOMER
- **Ticket Management**: Create, update, assign, and track tickets
- **SLA Monitoring**: Automatic SLA breach detection
- **File Attachments**: Upload and manage ticket attachments
- **Knowledge Base**: Public knowledge base articles
- **Analytics Dashboard**: Comprehensive reports and charts
- **Real-time Comments**: WhatsApp-style chat interface for ticket conversations
- **Internal Notes**: Private comments visible only to agents/admins

## Tech Stack

### Backend
- Node.js + Express.js
- MySQL with Prisma ORM
- JWT Authentication
- Multer for file uploads
- Bcrypt for password hashing

### Frontend
- React 18 with Vite
- Tailwind CSS
- Framer Motion (Animations)
- Recharts (Analytics)
- React Router DOM
- Axios
- Lucide React (Icons)
- React Hot Toast

## Quick Start

### Prerequisites
- Node.js (v18+)
- MySQL (v8+)
- npm or yarn

### Backend Setup

1. Navigate to the server directory:
```bash
cd server
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file:
```env
DATABASE_URL="mysql://user:password@localhost:3306/helpdesk_db"
JWT_SECRET="your-super-secret-jwt-key-change-in-production"
PORT=5000
NODE_ENV=development
```

4. Generate Prisma Client:
```bash
npm run prisma:generate
```

5. Run migrations:
```bash
npm run prisma:migrate
```

6. Seed the database:
```bash
npm run prisma:seed
```

7. Start the server:
```bash
npm run dev
```

### Frontend Setup

1. Navigate to the client directory:
```bash
cd client
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

## Default Credentials

- **Email:** admin@helpdesk.com
- **Password:** admin123
- **Role:** SUPER_ADMIN

## Project Structure

```
helpdesk-application/
├── server/
│   ├── config/
│   │   └── database.js
│   ├── middleware/
│   │   ├── auth.js
│   │   └── sla.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── users.js
│   │   ├── tickets.js
│   │   ├── attachments.js
│   │   ├── kb.js
│   │   ├── reports.js
│   │   └── sla.js
│   ├── utils/
│   │   └── notifications.js
│   ├── prisma/
│   │   ├── schema.prisma
│   │   └── seed.js
│   ├── uploads/
│   └── index.js
└── client/
    ├── src/
    │   ├── components/
    │   │   ├── Layout.jsx
    │   │   ├── Sidebar.jsx
    │   │   ├── StatsCard.jsx
    │   │   ├── DataTable.jsx
    │   │   └── TicketChat.jsx
    │   ├── contexts/
    │   │   └── AuthContext.jsx
    │   ├── pages/
    │   │   ├── Login.jsx
    │   │   ├── Dashboard.jsx
    │   │   ├── Tickets.jsx
    │   │   ├── TicketDetails.jsx
    │   │   ├── NewTicket.jsx
    │   │   ├── Users.jsx
    │   │   ├── KnowledgeBase.jsx
    │   │   └── Reports.jsx
    │   ├── utils/
    │   │   ├── api.js
    │   │   └── cn.js
    │   ├── App.jsx
    │   ├── main.jsx
    │   └── index.css
    └── package.json
```

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new customer
- `POST /api/auth/login` - Login
- `GET /api/auth/me` - Get current user

### Users
- `GET /api/users` - Get all users (Admin/Manager)
- `POST /api/users` - Create user (Admin)
- `PUT /api/users/:id` - Update user (Admin)
- `DELETE /api/users/:id` - Delete user (Admin)

### Tickets
- `GET /api/tickets` - Get all tickets (role-based filtering)
- `GET /api/tickets/:id` - Get single ticket
- `POST /api/tickets` - Create ticket (Customer)
- `PUT /api/tickets/:id` - Update ticket (Agent/Admin)
- `POST /api/tickets/:id/comments` - Add comment

### Attachments
- `POST /api/attachments/:ticketId` - Upload file
- `GET /api/attachments/:ticketId` - Get ticket attachments
- `DELETE /api/attachments/:id` - Delete attachment

### Knowledge Base
- `GET /api/kb` - Get all articles (public)
- `GET /api/kb/:id` - Get single article
- `POST /api/kb` - Create article (Admin)
- `PUT /api/kb/:id` - Update article (Admin)
- `DELETE /api/kb/:id` - Delete article (Admin)

### Reports
- `GET /api/reports/dashboard` - Get dashboard statistics
- `GET /api/reports/sla` - Get SLA statistics

### SLA
- `GET /api/sla` - Get all SLAs
- `PUT /api/sla/:id` - Update SLA

## Design Philosophy

- **Color Palette**: Slate & Blue (corporate, clean, modern)
- **UI/UX**: Smooth transitions, skeleton loaders, toast notifications
- **Components**: ShadCN UI inspired (Cards, Tables, Dialogs)
- **Animations**: Framer Motion for smooth transitions

## License

MIT

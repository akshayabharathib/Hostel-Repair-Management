# Hostel Repair Management System

A comprehensive web application for managing hostel repair requests. Students can submit and track complaints, while administrators can manage and update repair statuses.

## Features

- **User Authentication**
  - Student registration with profile details (name, hostel block, room number, email, phone)
  - Login/logout functionality
  - JWT-based session management

- **Student Dashboard**
  - Overview of submitted complaints
  - Statistics (total, pending, in progress, repaired)
  - Recent complaints list

- **Complaint Management**
  - Submit new repair requests
  - Categories: Electrical, Plumbing, Furniture, Internet/WiFi, Cleaning, Other
  - Priority levels: Low, Medium, High
  - Optional image upload
  - Track complaint status
  - Search and filter complaints

- **Admin Panel**
  - View all complaints
  - Update complaint status
  - Assign technicians
  - Add repair notes
  - Manage users
  - View technicians

- **Additional Features**
  - Dark mode support
  - Responsive design
  - Toast notifications
  - Pagination
  - Complaint tracking ID

## Tech Stack

- **Frontend**: React + Vite + Tailwind CSS
- **Backend**: Supabase (PostgreSQL + Auth)
- **Icons**: Lucide React
- **Routing**: React Router DOM
- **State Management**: TanStack Query

## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn
- Supabase account

### Installation

1. Clone the repository
```bash
git clone <repository-url>
cd hostel-repair-management
```

2. Install dependencies
```bash
npm install
```

3. Set up environment variables
Create a `.env` file in the root directory:
```env
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

4. Start the development server
```bash
npm run dev
```

5. Build for production
```bash
npm run build
```

## Database Schema

### Profiles Table
- `id`: UUID (references auth.users)
- `name`: TEXT
- `email`: TEXT
- `phone`: TEXT
- `hostel_block`: TEXT
- `room_number`: TEXT
- `role`: TEXT (student/admin)

### Complaints Table
- `id`: UUID
- `tracking_id`: TEXT (unique, auto-generated)
- `title`: TEXT
- `description`: TEXT
- `category`: TEXT (electrical/plumbing/furniture/internet_wifi/cleaning/other)
- `priority`: TEXT (low/medium/high)
- `status`: TEXT (pending/assigned/in_progress/repaired/closed)
- `hostel_block`: TEXT
- `room_number`: TEXT
- `image_url`: TEXT (optional)
- `repair_notes`: TEXT
- `created_by`: UUID (references profiles)
- `assigned_to`: TEXT
- `created_at`: TIMESTAMPTZ
- `updated_at`: TIMESTAMPTZ
- `repaired_at`: TIMESTAMPTZ

## API Endpoints

All data operations are handled through Supabase client with Row Level Security (RLS) policies.

## User Roles

### Student
- Register and login
- Submit complaints
- View own complaints
- Update profile settings

### Admin
- View all complaints
- Update complaint status
- Assign technicians
- Add repair notes
- Delete complaints
- View all users

## Creating an Admin Account

To create an admin account:
1. Register a new account with email `admin@hostel.edu`
2. In Supabase SQL editor, update the role:
```sql
UPDATE profiles SET role = 'admin' WHERE email = 'admin@hostel.edu';
```

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## License

MIT License

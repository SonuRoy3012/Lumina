# Video Editor Web Application

A modern, full-featured video editing web application built with React, Vite, and Supabase. Create, edit, and manage video projects with an intuitive timeline-based editor.

## 🎬 Features

### Video Editor
- **Timeline-based editing** - Drag and drop clips to reorder
- **Real-time preview** - See your video as you edit
- **Multiple media types** - Support for images, videos, and audio
- **Playback controls** - Play, pause, skip between clips
- **Timeline scrubbing** - Seek to any position
- **Clip editing** - Adjust duration, apply effects, add transitions

### Editing Tools
- **Trim** - Adjust clip duration
- **Effects** - Blur, brightness, contrast, saturation, grayscale, sepia
- **Transitions** - Fade, dissolve, wipe, slide, zoom
- **Audio** - Volume control, fade in/out
- **Text** - Add text overlays with customization

### Project Management
- **Save projects** - Save work-in-progress
- **Resume editing** - Continue where you left off
- **Projects library** - View all saved projects
- **Delete projects** - Remove unwanted projects

### User Authentication
- **Email/Password** - Secure authentication
- **Email verification** - OTP-based verification
- **Protected routes** - Secure access control
- **User profiles** - Manage account settings

### Dashboard
- **Dynamic statistics** - Active projects, team members, tasks
- **Quick actions** - Create new project, view projects, analytics
- **Recent activity** - Track your progress

## 🚀 Tech Stack

### Frontend
- **React 18** - UI framework
- **Vite** - Build tool and dev server
- **React Router** - Navigation
- **Zustand** - State management
- **Framer Motion** - Animations
- **Tailwind CSS** - Styling

### Backend
- **Supabase** - Backend as a Service
  - Authentication
  - PostgreSQL database
  - Row Level Security
  - Storage (for file uploads)

## 📦 Installation

### Prerequisites
- Node.js 18+ and npm
- Supabase account

### 1. Clone the Repository
```bash
git clone <your-repo-url>
cd python
```

### 2. Install Dependencies
```bash
cd frontend
npm install
```

### 3. Setup Environment Variables
Create `frontend/.env` file:
```env
VITE_SUPABASE_URL=your-supabase-project-url
VITE_SUPABASE_ANON_KEY=your-supabase-anon-key
```

### 4. Setup Supabase Database

#### Run SQL Scripts in Supabase SQL Editor:

**1. Create profiles table:**
```bash
frontend/supabase/create_profiles_table.sql
```

**2. Create projects table:**
```bash
frontend/supabase/FIXED_SETUP.sql
```

### 5. Start Development Server
```bash
npm run dev
```

Open http://localhost:3000

## 📁 Project Structure

```
python/
├── frontend/
│   ├── src/
│   │   ├── components/      # Reusable components
│   │   │   ├── Navbar.jsx
│   │   │   └── Sidebar.jsx
│   │   ├── pages/           # Page components
│   │   │   ├── Home.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   ├── NewProject.jsx
│   │   │   ├── VideoEditor.jsx
│   │   │   └── Projects.jsx
│   │   ├── store/           # State management
│   │   │   ├── useAuthStore.js
│   │   │   └── useProjectStore.js
│   │   ├── lib/             # Utilities
│   │   │   └── supabaseClient.js
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── supabase/            # Database schemas
│   │   ├── create_profiles_table.sql
│   │   ├── FIXED_SETUP.sql
│   │   └── create_storage_bucket.sql
│   ├── public/
│   ├── package.json
│   └── vite.config.js
├── .gitignore
└── README.md
```

## 🎯 Usage

### Creating a Project
1. Login to your account
2. Click "New Project" on Dashboard
3. Enter project name and description
4. Select images/videos from your computer
5. Click "Continue to Editor"

### Editing Video
1. **Arrange clips** - Drag to reorder in timeline
2. **Adjust duration** - Select clip → Trim tab → Change duration
3. **Apply effects** - Select clip → Effects tab → Choose effect
4. **Add transitions** - Select clip → Transitions tab
5. **Preview** - Click Play button to watch
6. **Save** - Click Save button to save progress

### Managing Projects
1. Go to "Projects" page
2. View all saved projects
3. Click "Edit" to resume editing
4. Click "Delete" to remove project

## 🔐 Database Schema

### profiles
- `id` - UUID (primary key)
- `email` - TEXT
- `full_name` - TEXT
- `avatar_url` - TEXT
- `created_at` - TIMESTAMPTZ
- `updated_at` - TIMESTAMPTZ

### projects
- `id` - UUID (primary key)
- `user_id` - UUID (foreign key)
- `name` - TEXT
- `description` - TEXT
- `status` - TEXT
- `timeline_data` - JSONB (video timeline)
- `playback_time` - NUMERIC (playback position)
- `thumbnail_url` - TEXT
- `created_at` - TIMESTAMPTZ
- `updated_at` - TIMESTAMPTZ

## 🛠️ Development

### Available Scripts

```bash
# Start dev server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Lint code
npm run lint
```

## 📝 Documentation

- [Setup Guide](SETUP_GUIDE.md)
- [Video Editor Guide](VIDEO_EDITOR_GUIDE.md)
- [Video Playback Update](VIDEO_PLAYBACK_UPDATE.md)
- [Project Save Guide](PROJECT_SAVE_GUIDE.md)
- [Storage Setup Guide](STORAGE_SETUP_GUIDE.md)

## 🐛 Known Issues

### Blob URLs
- File URLs are temporary (session-only)
- Files need to be re-selected after page reload
- Future: Upload to Supabase Storage for persistence

### Video Export
- Export functionality not yet implemented
- Requires FFmpeg.js or server-side processing

## 🔜 Roadmap

- [ ] Implement video export/rendering
- [ ] Add file persistence to Supabase Storage
- [ ] Real-time collaboration
- [ ] More effects and transitions
- [ ] Audio mixing
- [ ] Text animation
- [ ] Video templates
- [ ] Mobile responsive editor

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is open source and available under the MIT License.

## 👨‍💻 Author

Built with ❤️ by [Your Name]

## 🙏 Acknowledgments

- React team for the amazing framework
- Supabase for the backend infrastructure
- Vite for the blazing fast build tool
- Tailwind CSS for the utility-first styling

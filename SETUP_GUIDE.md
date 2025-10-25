# Dashboard Stats Setup Guide

## What Changed

The dashboard now displays **real data** instead of hardcoded numbers. All stats (Active Projects, Team Members, Completed Tasks, In Progress) will start at **0** and increase as you add data.

## Current Status

✅ **Frontend Code Updated**
- Created `useProjectStore.js` - Manages projects, tasks, and team members
- Updated `Dashboard.jsx` - Now fetches and displays real-time stats
- Stats will show 0 until you add data

⚠️ **Database Setup Required**
You need to create the database tables in Supabase for the stats to work properly.

## Database Setup Steps

### Step 1: Access Supabase SQL Editor

1. Go to your Supabase project dashboard at https://supabase.com
2. Click on your project
3. Navigate to **SQL Editor** in the left sidebar
4. Click **New Query**

### Step 2: Run the SQL Script

1. Open the file: `frontend/supabase/create_project_tables.sql`
2. Copy the entire contents
3. Paste it into the Supabase SQL Editor
4. Click **Run** (or press Ctrl+Enter)

### Step 3: Verify Tables Created

1. Go to **Table Editor** in the left sidebar
2. You should see these new tables:
   - `projects`
   - `tasks`
   - `team_members`

## How It Works

### Dashboard Stats

The dashboard now calculates stats from real data:

- **Active Projects**: Count of projects with `status = 'active'`
- **Team Members**: Total count of team members
- **Completed Tasks**: Count of tasks with `status = 'completed'`
- **In Progress**: Count of tasks with `status = 'in_progress'`

### Adding Data (Future Features)

Once the database is set up, you can add data through:

1. **Projects**: Create new projects (will need a project creation UI)
2. **Tasks**: Add tasks to projects (will need a task management UI)
3. **Team Members**: Invite team members (will need a team management UI)

For now, you can manually add test data through Supabase:

1. Go to **Table Editor** in Supabase
2. Select a table (e.g., `projects`)
3. Click **Insert** → **Insert row**
4. Fill in the fields:
   - `user_id`: Your user ID (from auth.users table)
   - `name`: "Test Project"
   - `status`: "active"
5. Click **Save**

The dashboard will automatically update to show the new data!

## Testing

After setting up the database:

1. The dashboard should show all stats as **0**
2. Add a test project in Supabase Table Editor
3. Refresh the dashboard - Active Projects should show **1**
4. Add a test task with status "completed"
5. Refresh - Completed Tasks should show **1**

## Next Steps

To make the app fully functional, you'll need to create:

1. **Project Management Page** - Create, view, edit, delete projects
2. **Task Management Page** - Create, view, edit, delete tasks
3. **Team Management Page** - Add, view, remove team members

Would you like me to create any of these pages?

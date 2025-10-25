# Storage Setup Guide for File Uploads

This guide will help you set up Supabase Storage for uploading images, videos, and audio files in your projects.

## Step 1: Create Database Table

1. Go to your Supabase project dashboard
2. Navigate to **SQL Editor**
3. Open the file: `frontend/supabase/create_storage_bucket.sql`
4. Copy and paste the SQL content
5. Click **Run** to create the `project_files` table

## Step 2: Create Storage Bucket

### Via Supabase Dashboard (Recommended)

1. Go to **Storage** in the left sidebar
2. Click **Create a new bucket**
3. Configure the bucket:
   - **Name**: `project-files`
   - **Public bucket**: Toggle ON (files will be publicly accessible)
   - **File size limit**: 50 MB (or adjust as needed)
   - **Allowed MIME types**: Leave empty or specify: `image/*,video/*,audio/*`
4. Click **Create bucket**

## Step 3: Set Up Storage Policies

After creating the bucket, you need to set up Row Level Security policies:

1. In the Storage section, click on your `project-files` bucket
2. Go to **Policies** tab
3. Click **New Policy**

### Policy 1: Allow Upload (INSERT)

- **Policy name**: Users can upload project files
- **Policy definition**: `SELECT`
- **Target roles**: `authenticated`
- **USING expression**:
  ```sql
  bucket_id = 'project-files'
  ```
- Click **Review** → **Save policy**

### Policy 2: Allow Read (SELECT)

- **Policy name**: Users can view project files
- **Policy definition**: `SELECT`
- **Target roles**: `authenticated`
- **USING expression**:
  ```sql
  bucket_id = 'project-files'
  ```
- Click **Review** → **Save policy**

### Policy 3: Allow Delete (DELETE)

- **Policy name**: Users can delete project files
- **Policy definition**: `DELETE`
- **Target roles**: `authenticated`
- **USING expression**:
  ```sql
  bucket_id = 'project-files'
  ```
- Click **Review** → **Save policy**

### Policy 4: Allow Update (UPDATE)

- **Policy name**: Users can update project files
- **Policy definition**: `UPDATE`
- **Target roles**: `authenticated`
- **USING expression**:
  ```sql
  bucket_id = 'project-files'
  ```
- Click **Review** → **Save policy**

## Step 4: Verify Setup

1. Go to **Storage** → **project-files**
2. Check that all 4 policies are active
3. Try uploading a test file manually to verify permissions

## Step 5: Test the Feature

1. Go to your app at http://localhost:3000
2. Login to your account
3. Click on **New Project** from the dashboard
4. Fill in project details
5. Upload some test files (images, videos, or audio)
6. Click **Create Project**
7. Check Supabase Storage to see your uploaded files

## File Organization

Files are organized in the storage bucket as follows:

```
project-files/
  └── {project-id}/
      ├── images/
      │   ├── {timestamp}-{random}.jpg
      │   └── {timestamp}-{random}.png
      ├── videos/
      │   └── {timestamp}-{random}.mp4
      └── audios/
          └── {timestamp}-{random}.mp3
```

## Supported File Types

### Images
- JPEG (.jpg, .jpeg)
- PNG (.png)
- GIF (.gif)
- WebP (.webp)
- SVG (.svg)
- BMP (.bmp)

### Videos
- MP4 (.mp4)
- WebM (.webm)
- MOV (.mov)
- AVI (.avi)

### Audio
- MP3 (.mp3)
- WAV (.wav)
- OGG (.ogg)
- M4A (.m4a)

## Troubleshooting

### Error: "new row violates row-level security policy"
- Make sure you've created all 4 storage policies
- Verify you're logged in as an authenticated user
- Check that the bucket name is exactly `project-files`

### Error: "Failed to upload file"
- Check file size (must be under the limit you set)
- Verify file type is allowed
- Check browser console for detailed error messages

### Files not showing up
- Verify the `project_files` table exists
- Check that the project was created successfully
- Look in Supabase Storage → project-files to see uploaded files

## Security Notes

- Files are organized by project ID, preventing unauthorized access
- Row Level Security ensures users can only access their own project files
- File metadata is stored in the database for easy retrieval
- Public URLs are generated for easy sharing (if public bucket)

## Next Steps

After setup is complete, you can:
1. Create projects with file uploads
2. View uploaded files in project details
3. Delete files when needed
4. Download files from the storage bucket

For private files, set the bucket to private and generate signed URLs for temporary access.

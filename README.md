# Student Face Recognition System

A complete web-based student management system with face recognition capabilities.

## Features

- **Role-Based Access Control**
  - Admin: Full student management
  - Student: View own profile only

- **Face Recognition**
  - Browser-based face detection using face-api.js
  - Upload photo detection
  - Live camera detection
  - 128-dimensional face embeddings

- **Student Management (Admin)**
  - Add, edit, delete students
  - Search and filter
  - Complete CRUD operations

- **Responsive Design**
  - Works on desktop, tablet, and mobile
  - Bootstrap 5 framework
  - Modern UI/UX

## Tech Stack

- **Backend**: Node.js, Express.js
- **Database**: SQLite3
- **Authentication**: JWT, bcrypt
- **Frontend**: HTML5, CSS3, JavaScript
- **Face Recognition**: face-api.js (browser-based)
- **UI Framework**: Bootstrap 5
- **Icons**: Font Awesome

## Installation

### 1. Install Dependencies

```bash
npm install
```

### 2. Download Face-API Models

Download these files from https://github.com/vladmandic/face-api/tree/master/model
and place them in `/public/models/` directory:

- tiny_face_detector_model-weights_manifest.json
- tiny_face_detector_model-shard1
- face_landmark_68_model-weights_manifest.json
- face_landmark_68_model-shard1
- face_recognition_model-weights_manifest.json
- face_recognition_model-shard1

### 3. Configure Environment

Edit `.env` file if needed (default settings work fine for development)

### 4. Start Server

```bash
npm start
```

Server will run on http://localhost:3000

## Default Admin Credentials

```
Username: admin
Password: admin123
```

## Project Structure

```
student-face-recognition/
├── config/                 # Database and auth configuration
├── middleware/             # Auth and upload middleware
├── routes/                 # API routes
├── services/               # Face recognition service
├── public/                 # Static files
│   ├── css/               # Stylesheets
│   ├── js/                # JavaScript files
│   └── models/            # Face-API models (download separately)
├── views/                  # HTML pages
│   ├── student/           # Student dashboard
│   └── admin/             # Admin dashboard
├── uploads/               # Uploaded student photos
├── server.js              # Main server file
└── package.json           # Dependencies
```

## API Endpoints

### Authentication
- `POST /api/auth/signup` - Student registration
- `POST /api/auth/login` - Login
- `GET /api/auth/verify` - Verify token
- `POST /api/auth/logout` - Logout

### Students
- `GET /api/students` - Get all students (admin)
- `GET /api/students/:id` - Get single student
- `POST /api/students` - Add student (admin)
- `PUT /api/students/:id` - Update student (admin)
- `DELETE /api/students/:id` - Delete student (admin)
- `GET /api/students/me/profile` - Get own profile (student)

### Detection
- `POST /api/detection/search` - Search by face descriptor
- `POST /api/detection/live` - Live camera detection

## Usage

### For Students

1. Go to http://localhost:3000
2. Click "Sign Up"
3. Fill registration form with photo
4. System will detect face and register
5. Login to view profile

### For Admin

1. Login with admin credentials
2. Access admin dashboard
3. Manage students (add/edit/delete)
4. Use face detection features

## Face Recognition Flow

1. **Registration**:
   - Student uploads photo
   - Browser runs face-api.js
   - Extracts 128-dimensional descriptor
   - Sends descriptor + photo to server
   - Server stores both in database

2. **Detection**:
   - Upload query photo or use camera
   - Browser extracts descriptor
   - Sends to server
   - Server compares with all stored descriptors
   - Returns best match

## Security

- Passwords hashed with bcrypt
- JWT token authentication
- Role-based access control
- File upload validation
- SQL injection prevention

## Troubleshooting

### Models Not Loading
- Ensure models are in `/public/models/` directory
- Check browser console for errors
- Models must be accessible via HTTP

### Face Not Detected
- Ensure clear, well-lit photo
- Only one face in photo
- Face clearly visible
- Try different photo

### Database Errors
- Delete `database.db` file and restart server
- Tables will be recreated automatically

## Development

```bash
# Install nodemon for development
npm install -g nodemon

# Run in dev mode
npm run dev
```

## License

MIT

## Support

For issues or questions, please create an issue in the repository.

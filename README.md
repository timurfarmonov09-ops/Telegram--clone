# 📱 Telegram Clone - Full Stack Real-time Chat Application

A full-featured Telegram clone built with modern web technologies, featuring real-time messaging, group chats, file sharing, and more.

## 🌟 Features

### ✅ Authentication
- Phone number authentication (auto-creates account)
- JWT token-based authentication
- Secure password hashing with bcrypt

### 💬 Messaging
- Real-time messaging with Socket.io
- Private chats
- Group chats with admin controls
- Message read receipts (single/double check marks)
- Typing indicators
- Online/offline status with last seen
- Message history with pagination

### 📁 File Sharing
- Image upload and display (10MB limit)
- Video upload with player (50MB limit)
- Document sharing (PDF, DOC, XLS, PPT, ZIP, etc. - 100MB limit)
- File download functionality
- Upload progress indicators

### 👥 User Features
- User search
- Profile management (name, username, bio, avatar)
- Online status tracking
- Last seen timestamps

### 🔔 Notifications
- Unread message count badges
- Real-time notification updates
- Chat-specific unread counts

### ⚙️ Settings
- Privacy settings (last seen, profile photo, read receipts)
- Notification preferences
- Theme selection (Light/Dark/Auto)

### 🎨 UI/UX
- Professional Telegram-style dark theme
- Responsive design
- Smooth animations and transitions
- Message grouping
- Smart scroll behavior
- Scroll to bottom button

## 🛠️ Tech Stack

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **Socket.io** - Real-time communication
- **MongoDB** - Database (with Mongoose ODM)
- **JWT** - Authentication
- **Multer** - File upload handling
- **bcrypt** - Password hashing

### Frontend
- **React** - UI library
- **TypeScript** - Type safety
- **Vite** - Build tool
- **Tailwind CSS** - Styling
- **Socket.io Client** - Real-time updates
- **Axios** - HTTP client
- **Lucide React** - Icons
- **React Hot Toast** - Notifications

## 📦 Installation

### Prerequisites
- Node.js (v16 or higher)
- MongoDB Atlas account (or local MongoDB)
- npm or yarn

### 1. Clone the repository
```bash
git clone https://github.com/timurfarmonov09-ops/Telegram--clone.git
cd Telegram--clone
```

### 2. Install dependencies
```bash
# Install root dependencies
npm install

# Install server dependencies
cd server
npm install

# Install client dependencies
cd ../client
npm install
```

### 3. Configure environment variables

**Server (.env)**
```env
PORT=3001
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
CLIENT_URL=http://localhost:5173
```

**Client (.env)**
```env
VITE_API_URL=http://localhost:3001
```

### 4. Start the application
```bash
# From root directory
npm run dev
```

This will start:
- Backend server on http://localhost:3001
- Frontend on http://localhost:5173 (or 5174 if 5173 is busy)

## 📖 Usage

### Test Users
The application automatically creates test users on first run:
- +998901234567 - Alisher Navoiy
- +998901234568 - Mirzo Ulug'bek
- +998901234569 - Abdulla Qodiriy
- +998901234570 - Hamid Olimjon
- +998901234571 - Oybek Malikov

### Login
1. Enter any phone number (e.g., +998901234567)
2. Account will be auto-created if it doesn't exist
3. Start chatting!

### Creating Group Chats
1. Click "New Group" button in sidebar
2. Enter group name and description
3. Search and select members
4. Click "Create"

### Sending Files
- **Images/Videos**: Click the image icon
- **Documents**: Click the paperclip icon
- Add optional caption and send

## 🏗️ Project Structure

```
telegram-clone/
├── client/                 # Frontend React application
│   ├── src/
│   │   ├── components/    # React components
│   │   │   ├── auth/      # Authentication components
│   │   │   ├── chat/      # Chat components
│   │   │   ├── profile/   # Profile components
│   │   │   └── settings/  # Settings components
│   │   ├── hooks/         # Custom React hooks
│   │   ├── services/      # API services
│   │   ├── types/         # TypeScript types
│   │   └── App.tsx        # Main app component
│   └── package.json
│
├── server/                # Backend Node.js application
│   ├── database/          # Database configurations
│   ├── models/            # Mongoose models
│   ├── routes/            # Express routes
│   ├── uploads/           # File uploads directory
│   └── index.js           # Server entry point
│
└── package.json           # Root package.json
```

## 🔌 API Endpoints

### Authentication
- `POST /api/auth/phone-register` - Phone authentication
- `POST /api/auth/login` - Login
- `GET /api/auth/me` - Get current user

### Chats
- `GET /api/chats/my` - Get user's chats
- `POST /api/chats/create` - Create private chat
- `POST /api/chats/create-group` - Create group chat
- `PUT /api/chats/:id/add-members` - Add members to group
- `PUT /api/chats/:id/remove-member` - Remove member from group
- `PUT /api/chats/:id/leave` - Leave group

### Messages
- `GET /api/messages/:chatId` - Get messages
- `POST /api/messages/send` - Send text message
- `POST /api/messages/send-image` - Send image
- `POST /api/messages/send-video` - Send video
- `POST /api/messages/send-file` - Send file
- `PUT /api/messages/:chatId/read` - Mark messages as read

### Users
- `GET /api/users/search` - Search users

### Profile
- `GET /api/profile/me` - Get profile
- `PUT /api/profile/update` - Update profile
- `PUT /api/profile/photo` - Upload profile photo
- `DELETE /api/profile/photo` - Delete profile photo

### Settings
- `GET /api/settings` - Get settings
- `PUT /api/settings` - Update settings

## 🔄 Socket.io Events

### Client → Server
- `user-online` - User comes online
- `join-chat` - Join chat room
- `leave-chat` - Leave chat room
- `send-message` - Send message
- `typing-start` - Start typing
- `typing-stop` - Stop typing

### Server → Client
- `user-status-changed` - User online/offline status
- `new-message` - New message received
- `user-typing` - User typing status
- `messages-read` - Messages marked as read
- `unread-count-update` - Unread count changed

## 🎯 Key Features Implementation

### Real-time Updates
- Socket.io for instant message delivery
- Online status tracking
- Typing indicators
- Read receipts

### File Upload
- Multer middleware for handling multipart/form-data
- Separate storage for images, videos, and documents
- Progress tracking during upload
- File type validation and size limits

### Notifications
- Unread message count per chat
- Real-time badge updates
- Reset on chat open

### Security
- JWT authentication
- Password hashing
- Input validation
- File type restrictions
- Rate limiting

## 🚀 Deployment

### Backend (Heroku/Railway/Render)
1. Set environment variables
2. Deploy from GitHub
3. Ensure MongoDB Atlas is accessible

### Frontend (Vercel/Netlify)
1. Build the client: `npm run build`
2. Deploy the `dist` folder
3. Set VITE_API_URL to your backend URL

## 📝 License

MIT License - feel free to use this project for learning or commercial purposes.

## 👨‍💻 Author

**Timur Farmonov**
- GitHub: [@timurfarmonov09-ops](https://github.com/timurfarmonov09-ops)

## 🙏 Acknowledgments

- Telegram for design inspiration
- Socket.io for real-time functionality
- MongoDB for flexible data storage
- React and TypeScript communities

## 📧 Contact

For questions or support, please open an issue on GitHub.

---

⭐ If you found this project helpful, please give it a star!

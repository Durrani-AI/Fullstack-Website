Terra Scenik* is a full-stack social media web application built for nature photography enthusiasts to share, discover, and engage with scenic nature content.
The platform enables users to connect with a community of nature lovers through a feature-rich, Instagram-style interface with a modern dark theme aesthetic.


*Tech Stack:* Node.js, Express.js, MongoDB Atlas, Vanilla JavaScript, HTML5, CSS3

---

## Key Features & Functionality

### 1. User Authentication & Session Management
- *User Registration:* Complete signup system with name, email, password, and optional bio
- *Secure Login:* Username/password authentication with server-side session management
- *Session Persistence:* 24-hour HTTP-only cookies for secure session handling
- *Auto-Login:* Automatic session restoration on page reload
- *Logout Functionality:* Clean session destruction with proper cleanup

### 2. User Profile Management
- *Profile Display:* View personal profile with name, email, bio, and profile picture
- *Profile Editing:* Modal-based profile editor for updating user information
- *Profile Picture Upload:* Image upload with Base64 encoding for avatar customization
- *Public Profiles:* View other users' profiles with their posts and follow status
- *Profile Navigation:* Click on any user to visit their full profile page

### 3. Post Creation & Management
- *Create Posts:* Share nature photos with captions and location information
- *Dual Image Sources:*
  - *Local Upload:* Upload images directly from device (up to 15MB)
  - *Unsplash Integration:* Search and select professional nature photos from Unsplash API
- *File Management:* Server-side image storage using Multer in user-specific directories
- *Edit Posts:* Update captions, locations, and images of existing posts
- *Delete Posts:* Remove posts with confirmation dialogs
- *My Posts Section:* View and manage all personal posts on profile page

### 4. Social Feed System
- *Personalized Feed:* Display posts only from followed users
- *Chronological Ordering:* Posts sorted by newest first
- *Rich Post Cards:* Display user avatar, username, timestamp, image, caption, location
- *Like System:* Toggle likes on posts with real-time count updates
- *Empty State Handling:* Helpful messages when feed is empty

### 5. Follow/Unfollow System
- *Follow Users:* Build your network by following other users
- *Unfollow Users:* Remove users from your following list with confirmation
- *Following List:* View complete list of users you follow on profile page
- *Follow Status Indication:* Visual feedback showing follow state on profiles
- *Protection:* Cannot follow yourself with proper error handling

### 6. Search Functionality
- *Dual Search:* Search for both users and posts
- *User Search:* Find users by name or email with follow button
- *Post Search:* Search posts by caption or location content
- *Navbar Quick Search:* Search bar in navigation for quick access
- *Dedicated Search Page:* Full search interface with results display
- *Search History:* Persistent search history stored in localStorage (last 5 searches)
- *History Management:* View, reuse, or delete previous searches

### 7. User Interface & Experience
- *Dark Theme:* Professional dark color scheme with brown accents
- *Responsive Design:* Adapts to different screen sizes
- *Collapsible Sidebar:* Hover-triggered sidebar navigation for cleaner UI
- *Animated Transitions:* Smooth fade and slide animations
- *Toast Notifications:* Non-intrusive success/error notifications
- *Confirmation Dialogs:* Custom modal dialogs for destructive actions
- *Loading States:* Visual feedback during data fetching
- *Empty States:* Informative messages when no content available

### 8. Navigation System
- *Sidebar Navigation:* Icon-based sidebar with Feed, Search, Create, and Profile views
- *Navbar Navigation:* Top navigation with quick access links
- *Profile Picture Navigation:* Click navbar avatar to access profile
- *Back Navigation:* Return buttons from user profiles to feed
- *View Switching:* Smooth transitions between app sections

---

## Technical Architecture

### Backend (Node.js/Express.js)

#### Server Configuration
- Express.js web framework with modular architecture
- ES Module syntax for modern JavaScript features
- Environment variable management with dotenv
- Request logging middleware for debugging
- Static file serving for frontend assets

#### RESTful API Endpoints (15+ routes)
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /M01049109/users | User registration |
| GET | /M01049109/users?q= | Search users |
| POST | /M01049109/login | User authentication |
| GET | /M01049109/login | Check login status |
| DELETE | /M01049109/login | User logout |
| POST | /M01049109/contents | Create new post |
| GET | /M01049109/contents?q= | Search posts |
| PUT | /M01049109/contents/:id | Update post |
| DELETE | /M01049109/contents/:id | Delete post |
| GET | /M01049109/contents/my | Get user's own posts |
| GET | /M01049109/feed | Get personalized feed |
| POST | /M01049109/follow | Follow a user |
| DELETE | /M01049109/follow | Unfollow a user |
| GET | /M01049109/following | Get following list |
| PUT | /M01049109/users/profile | Update profile |
| PUT | /M01049109/users/profile-picture | Update avatar |
| GET | /M01049109/users/:email/profile | Get user's public profile |
| POST | /M01049109/contents/:id/like | Like a post |
| DELETE | /M01049109/contents/:id/like | Unlike a post |
| POST | /M01049109/upload | Upload image file |
| GET | /M01049109/unsplash | Proxy for Unsplash API |

#### Security Features
- Session-based authentication with express-session
- HTTP-only cookies to prevent XSS attacks
- Authentication middleware protecting private routes
- Input validation on all endpoints
- Ownership verification for edit/delete operations
- API key protection via server-side Unsplash proxy

#### File Upload System
- Multer middleware for multipart form handling
- 15MB file size limit
- User-specific upload directories (/Uploads/M01049109/)
- Unique filename generation with timestamps
- File extension preservation

### Database (MongoDB Atlas)

#### Collections
1. *users* - User accounts and profiles
   - name, email, password, bio, profilePicture, createdAt
   
2. *posts* - User-generated content
   - userId, userName, userEmail, caption, location, image_url, createdAt
   
3. *follows* - Social graph relationships
   - followerId, followerName, followingId, followingName, followingEmail, createdAt
   
4. *likes* - Post engagement tracking
   - userId, postId, createdAt

#### Database Features
- MongoDB Atlas cloud hosting with TLS encryption
- Efficient querying with regex search
- Relationship management across collections
- Automatic cascade updates for user data changes

### Frontend (Vanilla JavaScript)

#### Architecture
- Single-page application (SPA) architecture
- AJAX-based API communication using Fetch API
- Event-driven programming with DOM manipulation
- Modular code organization with clear sections
- Comprehensive commenting for code documentation

#### Key JavaScript Modules (~2000 lines)
- *Authentication Module:* Login, register, logout, session checking
- *Navigation Module:* View switching, sidebar toggle, back navigation
- *Feed Module:* Load feed, render posts, attach event listeners
- *Post Module:* Create, edit, delete posts, image preview
- *Profile Module:* Load profile, update profile, profile picture upload
- *Social Module:* Follow, unfollow, following list management
- *Search Module:* User/post search, search history, navbar search
- *Like Module:* Toggle like, update counts
- *Notification Module:* Toast notifications, confirmation dialogs
- *Unsplash Module:* Search, select, and integrate external images
- *Utility Functions:* Date formatting, HTML escaping, error handling

#### UI Components
- Responsive grid layouts
- Modal dialogs for editing
- Tab-based interfaces
- Loading spinners and states
- Image preview containers
- Card-based post display
- Avatar components with fallbacks

### Styling (CSS3)

#### Design System
- CSS Custom Properties (Variables) for theming
- Dark theme color palette with brown accents
- Consistent spacing and typography
- Responsive breakpoints for different devices

#### CSS Features (~2300 lines)
- Flexbox and Grid layouts
- CSS animations and transitions
- Hover and focus states
- Form styling with validation indicators
- Modal overlays with backdrop blur
- Scrollable containers
- Icon integration
- Custom scrollbar styling

---

## External API Integration

### Unsplash API
- *Purpose:* Access high-quality nature photography
- *Implementation:* Server-side proxy to protect API key
- *Features:* 
  - Keyword-based image search
  - Thumbnail and full-resolution URLs
  - Photographer attribution
  - 20 results per search

---

## Dependencies

### Production Dependencies
- *express* (v4.21.2) - Web application framework
- *mongodb* (v7.0.0) - MongoDB driver for Node.js
- *express-session* (v1.18.0) - Session middleware
- *multer* (v2.0.2) - File upload middleware
- *dotenv* (v17.2.3) - Environment variable management

### Development Dependencies
- *nodemon* (v3.0.1) - Development server with auto-restart

---

## Project Structure


CourseW2/
├── Code/
│   ├── index.html          # Main SPA HTML file (397 lines)
│   ├── package.json         # Project configuration
│   ├── .env                 # Environment variables (API keys)
│   ├── JS/
│   │   ├── app.js          # Frontend JavaScript (2049 lines)
│   │   └── server.js       # Backend Express server (1224 lines)
│   └── Style/
│       ├── style.css       # Complete styling (2286 lines)
│       └── icons/          # SVG icon assets
├── Uploads/
│   └── M01049109/          # User-uploaded images
└── database-dump/          # MongoDB export files


---

## Skills Demonstrated

### Backend Development
- RESTful API design and implementation
- Server-side session management
- Database design and querying (NoSQL/MongoDB)
- File upload handling and storage
- Third-party API integration
- Security best practices

### Frontend Development
- Single-page application architecture
- DOM manipulation and event handling
- Asynchronous JavaScript (Promises, async/await)
- Responsive CSS design
- User interface/experience design
- State management without frameworks

### Full-Stack Integration
- Client-server communication via AJAX
- JSON data exchange
- Authentication flow implementation
- Real-time UI updates
- Error handling across stack

### Software Engineering
- Clean code organization
- Comprehensive code commenting
- Modular architecture
- Version control awareness
- Environment configuration

---

## Summary Statistics

| Component | Lines of Code |
|-----------|---------------|
| HTML | 397 |
| CSS | 2,286 |
| Frontend JavaScript | 2,049 |
| Backend JavaScript | 1,224 |
| *Total* | *~5,956* |

| Feature Count | Number |
|---------------|--------|
| API Endpoints | 18+ |
| Database Collections | 4 |
| CSS Variables | 10+ |
| JavaScript Functions | 50+ |
| UI Views/Pages | 6 |

---

## Conclusion

Terra Scenik demonstrates comprehensive full-stack web development skills, combining modern frontend techniques with a robust Node.js/Express backend and MongoDB database. The application showcases the ability to build a complete social media platform from scratch, including user authentication, real-time interactions, file handling, and third-party API integration—all without relying on frontend frameworks, proving strong foundational JavaScript skills.

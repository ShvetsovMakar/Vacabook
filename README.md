# Vacabook

A social networking and blogging platform built with Flask, designed as a Yandex Lyceum project. Vacabook allows users to create accounts, share posts, connect with other users, and customize their experience with theme preferences.

## Features

- **User Authentication**: Secure user registration and login system
- **User Profiles**: Create and edit personalized user profiles with name, surname, birth date, and bio
- **Blogging**: Create and publish posts with titles, content, and categories
- **Social Feed**: Browse posts from all users in a unified feed
- **User Discovery**: View other users' profiles and their public information
- **Theme Support**: Switch between day and night modes for personalized viewing experience
- **Error Handling**: Comprehensive error pages for invalid users and 404 errors

## Technology Stack

- **Backend**: Python 3 with Flask web framework
- **Frontend**: HTML, CSS, and Jinja2 templating
- **Database**: SQLite
- **Authentication**: Flask-Login for session management

## Project Structure

```
Vacabook/
├── main.py                 # Main Flask application and routes
├── authentication/
│   └── user.py            # User authentication model
├── database/
│   └── config.py          # Database configuration and connection
├── templates/             # Jinja2 HTML templates
│   ├── index.html         # Landing page
│   ├── login.html         # Login page
│   ├── sign_up.html       # Registration page
│   ├── feed.html          # Post feed page
│   ├── create_post.html   # Post creation page
│   ├── edit_profile.html  # Profile editing page
│   ├── user_info.html     # User profile view page
│   ├── invalid_user.html  # Invalid user error page
│   ├── login_required.html# Authentication required page
│   └── page_not_found.html# 404 error page
├── static/                # Static assets (CSS, JavaScript, images)
└── .idea/                 # IDE configuration files
```

## Installation

### Prerequisites

- Python 3.7 or higher
- pip (Python package manager)

### Setup Instructions

1. **Clone the repository**:
   ```bash
   git clone https://github.com/ShvetsovMakar/Vacabook.git
   cd Vacabook
   ```

2. **Install dependencies**:
   Create a `requirements.txt` file with the following packages:
   ```
   Flask==2.0.0
   Flask-Login==0.6.0
   ```

   Then install:
   ```bash
   pip install -r requirements.txt
   ```

3. **Initialize the database**:
   Ensure your `database/config.py` is properly configured with SQLite connection settings.

4. **Run the application**:
   ```bash
   python main.py
   ```

   The application will start on `http://localhost:5000` by default.

## Usage

### Getting Started

1. **Create an Account**: Navigate to the sign-up page and create a new account with a username and password
2. **Log In**: Log in with your credentials to access the main feed
3. **View Feed**: Browse posts from all users on the feed page
4. **Create Posts**: Click "Create Post" to share your thoughts with a title, content, and category
5. **Edit Profile**: Customize your profile with personal information and bio
6. **Browse Users**: Click on usernames to view other users' profiles
7. **Customize Theme**: Switch between day and night modes in your preferences

### Routes Overview

| Route | Method | Description |
|-------|--------|-------------|
| `/` | GET | Landing page (redirects to feed if logged in) |
| `/sign_up` | GET, POST | User registration |
| `/login` | GET, POST | User login |
| `/feed` | GET, POST | Main feed with all posts |
| `/create_post` | POST | Create a new post (requires login) |
| `/edit_profile` | GET, POST | Edit user profile (requires login) |
| `/user/<username>` | GET | View user profile |
| `/logout` | GET | Log out current user |
| `/invalid_user` | GET | Error page for invalid users |

## Database Schema

The application uses SQLite with the following main tables:

### Users Table
- `id` - Unique user identifier
- `username` - Unique username (lowercase)
- `password` - User password
- `name` - User's first name
- `surname` - User's last name
- `birth_date` - User's birth date
- `about` - User biography
- `mode` - Theme preference (day/night)

### Posts Table
- `id` - Unique post identifier
- `title` - Post title
- `content` - Post content
- `category` - Post category
- `creation_date` - Date post was created
- `author_id` - ID of the post author (foreign key)

## Key Classes and Functions

### Post Class
Represents a blog post with the following attributes:
- `id` - Post identifier
- `title` - Post title
- `content` - Post content
- `category` - Post category
- `creation_date` - Date of creation
- `author` - Username of the post author

### Helper Functions

- `fetch_usernames()` - Retrieves all usernames from the database
- `string_to_date(string)` - Converts date strings to date objects
- `load_user(name)` - Flask-Login user loader function

## Development Notes

### Security Considerations

⚠️ **Important**: This is a Lyceum project and has several security considerations to address in production:
- Passwords are stored in plain text (should use hashing with bcrypt or similar)
- SQL queries use string formatting (vulnerable to SQL injection - use parameterized queries)
- Secret key is hardcoded (should use environment variables)

### Future Improvements

- Implement proper password hashing
- Add input validation and sanitization
- Improve error handling and user feedback
- Add following/friendship features
- Implement post comments and likes
- Add image upload support
- Implement search functionality
- Add post editing and deletion capabilities
- Create admin panel

## License

This project is created for Yandex Lyceum educational purposes.

## Author

**ShvetsovMakar** - [GitHub Profile](https://github.com/ShvetsovMakar)

## Contributing

This is an educational project. Contributions and improvements are welcome! Feel free to submit pull requests or open issues for bugs and feature requests.

---

**Note**: This project was created as part of the Yandex Lyceum curriculum. It serves as a learning exercise in web development with Flask and should be improved with production-ready security practices before any real-world deployment.

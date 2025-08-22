📖 Blogging Site – Mini Project

A Blogging Platform API built with Node.js, Express, and MongoDB.
This project implements core blogging features like author management, blog creation, publishing workflows, filtering, authentication, and authorization.

Designed as part of a mini-project to showcase REST API design, database modeling, authentication, and Postman testing.

🚀 Features
Phase I – Core Blogging APIs

Author Management

Create new authors with validation and unique emails.

Blog Management

Create new blogs for registered authors.

Get all published & non-deleted blogs (with filters by author, category, tags, subcategories).

Update blog details (title, body, tags, subcategories) and publish status.

Soft delete blogs by ID or query filters (category, tags, subcategories, author).

Phase II – Authentication & Authorization

JWT-based Login

Login with email & password to receive a secure token.

Authentication Middleware

Validates JWT tokens before accessing protected routes.

Authorization

Only blog owners can edit or delete their blogs.

🛠 Tech Stack

Backend Framework: Node.js with Express.js

Database: MongoDB with Mongoose ODM

Authentication: JWT (JSON Web Tokens)

Tools: Postman (API testing), bcrypt (password hashing)

📂 Database Models
👤 Author Model
{
  fname: { type: String, required: true },
  lname: { type: String, required: true },
  title: { type: String, enum: ["Mr", "Mrs", "Miss"], required: true },
  email: { type: String, required: true, unique: true, match: validEmailRegex },
  password: { type: String, required: true }
}

📝 Blog Model
{
  title: { type: String, required: true },
  body: { type: String, required: true },
  authorId: { type: ObjectId, ref: "Author", required: true },
  tags: [String],
  category: { type: String, required: true },
  subcategory: [String],
  createdAt: Date,
  updatedAt: Date,
  deletedAt: Date,
  isDeleted: { type: Boolean, default: false },
  publishedAt: Date,
  isPublished: { type: Boolean, default: false }
}

📌 API Endpoints
Author APIs

POST /authors → Create new author

Blog APIs

POST /blogs → Create a new blog (author must exist)

GET /blogs → Get all published blogs (with filters)

PUT /blogs/:blogId → Update blog details or publish status

DELETE /blogs/:blogId → Soft delete blog by ID

DELETE /blogs?filters → Soft delete blogs by query filters

Authentication

POST /login → Login and receive JWT token

🔐 Security

Passwords stored securely using hashing.

Protected routes secured via JWT tokens (x-api-key header).

Authorization ensures only the owner of a blog can modify/delete it.

🧪 Testing with Postman

Postman Collection created with endpoints:

Create Author

Create Blog

Get Blogs

Update Blog

Delete Blog

Login & Authentication

📸 Sample Response

✅ Success Response

{
  "status": true,
  "data": { }
}


❌ Error Response

{
  "status": false,
  "msg": "Error message here"
}

📊 Sample Blog Document
{
  "title": "How to win friends",
  "body": "Blog body",
  "tags": ["Book", "Friends", "Self help"],
  "category": "Book",
  "subcategory": ["Non fiction", "Self Help"],
  "isPublished": false,
  "publishedAt": "",
  "isDeleted": false,
  "deletedAt": "",
  "createdAt": "2021-09-17T04:25:07.803Z",
  "updatedAt": "2021-09-17T04:25:07.803Z"
}

📚 Setup & Run
1. Clone Repository
git clone https://github.com/your-username/Blogging-Site.git
cd Blogging-Site

2. Install Dependencies
npm install

3. Configure Environment

Create a .env file:

MONGODB_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/groupXDatabase
JWT_SECRET=yourSecretKey
PORT=3000

4. Run Server
npm start


Server runs at: http://localhost:3000/

# 📖 Blogging Site – Mini Project  

![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Express.js](https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)


A **RESTful Blogging API** built with **Node.js, Express, and MongoDB**.  
This project showcases **backend development, authentication, authorization, and CRUD operations** with Postman-tested APIs.  

---

## 📑 Table of Contents
- [🚀 Features](#-features)
- [🛠 Tech Stack](#-tech-stack)
- [📂 Database Models](#-database-models)
- [📌 API Endpoints](#-api-endpoints)
- [🔐 Security](#-security)
- [📚 Setup & Run](#-setup--run)
- [✅ Sample Response](#-sample-response)
- [🎥 Demo](#-demo)
- [👥 Contributors](#-contributors)

---

## 🚀 Features

### Phase I – Core Blogging APIs
- 👤 **Author Management**
  - Create authors with validation & unique emails
- 📝 **Blog Management**
  - Create blogs for registered authors  
  - Get all **published & non-deleted** blogs  
  - Filter blogs by **author, category, tags, subcategories**  
  - Update blogs (title, body, tags, subcategories, publish status)  
  - Soft delete blogs (by ID or query filters)

### Phase II – Authentication & Authorization
- 🔑 **JWT Authentication** (login with email & password)  
- 🛡 **Protected Routes** (secured with middleware)  
- ✅ **Authorization** (only blog owners can edit/delete their blogs)  

---

## 🛠 Tech Stack
- **Backend**: Node.js, Express.js  
- **Database**: MongoDB with Mongoose  
- **Authentication**: JWT (JSON Web Tokens)  
- **Other Tools**: bcrypt (password hashing), Postman (API testing)  

---

## 📂 Database Models

### 👤 Author Model
```js
{
  fname: { type: String, required: true },
  lname: { type: String, required: true },
  title: { type: String, enum: ["Mr", "Mrs", "Miss"], required: true },
  email: { type: String, required: true, unique: true },
  password: { type: String, required: true }
}

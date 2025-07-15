# Quick.ai - AI-Powered Content Creation SaaS Platform 🚀

Quick.ai is a comprehensive Software-as-a-Service (SaaS) platform built with the MERN stack (MongoDB, Express.js, React, Node.js), though this version uses NeonDB (PostgreSQL) instead of MongoDB. It leverages the power of various AI APIs to provide users with a suite of tools for content creation and enhancement. From writing articles and generating images to reviewing resumes, Quick.ai is your all-in-one solution for high-quality, AI-driven content.

[](https://saas-pi-silk.vercel.app/)

## ✨ Features

  * **User Authentication**: Secure sign-up and sign-in functionality using Clerk.
  * **AI Article Writer**: Generate high-quality, engaging articles on any topic.
  * **Blog Title Generator**: Create catchy and optimized titles for your blog posts.
  * **AI Image Generation**: Produce stunning visuals from text descriptions.
  * **Image Background Removal**: Effortlessly remove backgrounds from your images.
  * **Image Object Removal**: Seamlessly remove unwanted objects from photos.
  * **AI Resume Reviewer**: Get AI-powered feedback to improve your resume.
  * **Community Hub**: Share your creations with the community and browse published work.
  * **User Dashboard**: Track your creations and manage your account.
  * **Subscription Plans**: A tiered pricing model (Free/Premium) managed with Clerk.

-----

## 🛠️ Tech Stack

| Category      | Technology                                                                                                                                                                                          |
| :------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Frontend** | React, Vite, Tailwind CSS, React Router, Axios, Clerk React                                                                                                                                         |
| **Backend** | Node.js, Express.js                                                                                                                                                                                 |
| **Database** | Neon (Serverless PostgreSQL)                                                                                                                                                                        |
| **AI & APIs** | Google Gemini API, Clipdrop API, Cloudinary AI                                                                                                                                                      |
| **Auth** | Clerk                                                                                                                                                                                               |
| **Hosting** | Vercel                                                                                                                                                                                              |

-----

## ⚙️ Installation & Setup

Follow these steps to set up and run the project on your local machine.

### Prerequisites

  * [Node.js](https://nodejs.org/en) (v18 or later)
  * [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)

### 1\. Clone the Repository

```bash
git clone <your-repository-url>
cd <project-directory>
```

### 2\. Server Setup

First, let's get the backend server running.

**A. API Keys and Services Setup**

You'll need to sign up for the following services to get the required API keys:

1.  **NeonDB**: For the PostgreSQL database. [Sign up here](https://neon.tech).
2.  **Cloudinary**: For image storage and transformations. [Sign up here](https://cloudinary.com/users/register_free).
3.  **Clerk**: For user authentication and management. [Sign up here](https://clerk.com/).
4.  **Clipdrop API**: For AI image generation. [Get your API key here](https://clipdrop.co/apis).
5.  **Gemini API**: For text-based AI generation. [Get your API key here](https://aistudio.google.com/apikey).

**B. Environment Variables**

Navigate to the `server` directory and create a `.env` file. Add the following variables with the keys you obtained above.

```bash
# /server/.env

# NeonDB Database URL
DATABASE_URL="your_neon_database_connection_string"

# Cloudinary Credentials
CLOUDINARY_CLOUD_NAME="your_cloudinary_cloud_name"
CLOUDINARY_API_KEY="your_cloudinary_api_key"
CLOUDINARY_API_SECRET="your_cloudinary_api_secret"

# Clerk Secret Key
CLERK_SECRET_KEY="your_clerk_secret_key"

# AI Service API Keys
CLIPDROP_API_KEY="your_clipdrop_api_key"
GEMINI_API_KEY="your_gemini_api_key"

# Server Port
PORT=3000
```

**C. Database Setup**

Go to your Neon project dashboard and use the SQL Editor to run the following command to create the `creations` table.

```sql
CREATE TABLE creations (
    id SERIAL PRIMARY KEY,
    user_id TEXT NOT NULL,
    prompt TEXT NOT NULL,
    content TEXT NOT NULL,
    type TEXT NOT NULL,
    publish BOOLEAN DEFAULT FALSE,
    likes TEXT[] DEFAULT '{}',
    created_at TIMESTAMPTZ DEFAULT NOW(),
    updated_at TIMESTAMPTZ DEFAULT NOW()
);
```

**D. Install Dependencies and Run Server**

Open a terminal in the `server` directory and run the following commands:

```bash
# Install dependencies
npm install

# Run the server
npm run server
```

Your server should now be running on `http://localhost:3000`.

### 3\. Client Setup

Now, let's set up the frontend.

**A. Environment Variables**

Navigate to the `client` directory and create a `.env` file. Add your Clerk Publishable Key and the server URL.

```bash
# /client/.env

# Clerk Publishable Key
VITE_CLERK_PUBLISHABLE_KEY="your_clerk_publishable_key"

# Backend Server URL
VITE_BASE_URL="http://localhost:3000"
```

**B. Install Dependencies and Run Client**

Open a separate terminal in the `client` directory and run the following commands:

```bash
# Install dependencies
npm install

# Run the development server
npm run dev
```

Your React application should now be running. You can access it at the local URL provided by Vite (usually `http://localhost:5173`).

Happy Coding\! ✨

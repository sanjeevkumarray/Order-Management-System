# E-Commerce Application

## Overview
This project is a scalable and event-driven **E-Commerce Platform** built with **Node.js, Express, MongoDB, Redis, and AWS**. It provides a seamless shopping experience with features like **product management, user authentication, cart and wishlist management, order tracking, and a coupon system**. Additionally, it includes an **Order Processing System** that utilizes **AWS SQS for asynchronous order processing and AWS SES for email notifications**.

## Features
### 🔹 User Management
- User Registration, Login, Logout (JWT & Refresh Token Authentication)
- Forgot Password, OTP Verification, and Password Reset
- Admin and User Role Authentication

### 🔹 Product Management
- CRUD operations for products
- Wishlist functionality

### 🔹 Shopping Cart & Coupons
- Add/Remove Products from Cart
- Increment/Decrement Product Quantity
- Apply Coupons for Discounts

### 🔹 Order Management
- Create, Track, and Update Orders
- Inventory Check before Order Confirmation
- Asynchronous Order Processing via AWS SQS

### 🔹 Caching & Notifications
- Redis caching for quick data retrieval
- Email notifications via AWS SES

## API Endpoints
### 🔹 Authentication Routes (`/api/auth`)
- `POST /register` - User Registration
- `POST /login` - User Login
- `POST /refresh` - Refresh Access Token
- `POST /forgetPassword` - Forgot Password Flow
- `POST /verifyOtp` - Verify OTP for Password Reset
- `POST /changePassword` - Change Password

### 🔹 Product Routes (`/api/product`)
- `POST /` - Add New Product (Admin)
- `GET /getproduct` - Get All Products
- `GET /:id` - Get Product by ID
- `PUT /updateproduct/:id` - Update Product (Admin)
- `DELETE /deleteproduct/:id` - Delete Product (Admin)
- `POST /addToWishList/:productId` - Add to Wishlist

### 🔹 Cart Routes (`/api/cart`)
- `POST /addSingleProduct` - Add to Cart
- `DELETE /removeSingleProduct/:productId` - Remove from Cart
- `POST /decrement` - Decrease Product Quantity
- `POST /increment` - Increase Product Quantity
- `GET /wishlist` - Get User Wishlist

### 🔹 Order Routes (`/api/orders`)
- `POST /createorder` - Create Order
- `GET /myorders` - Get User Orders
- `GET /all` - Get All Orders (Admin)
- `PATCH /:id` - Update Order Status (Admin)

### 🔹 Coupon Routes (`/api/coupons`)
- `POST /` - Create Coupon
- `GET /` - Get All Coupons
- `PUT /:id` - Update Coupon
- `DELETE /:id` - Delete Coupon
- `POST /apply` - Apply Coupon

### 🔹 Other Routes
- **FAQs (`/api/faqs`)**: Manage FAQs
- **About Us (`/api/about`)**: Manage About Us Information

## 🛠️ Tech Stack
- **Backend:** Node.js, Express.js
- **Database:** MongoDB
- **Caching:** Redis
- **Authentication:** JWT (Access & Refresh Tokens)
- **Async Processing:** AWS SQS
- **Email Service:** AWS SES

## 🔧 Project Setup
### Prerequisites
- **Node.js** (v14+)
- **MongoDB** (Atlas or Local)

### Installation
```sh
# Clone the repository
git clone https://github.com/your-username/ecommerce-app.git
cd ecommerce-app

# Install dependencies
npm install

# Start Backend Server
cd backend
node index.js

# Start Frontend Server
cd frontend
npm run dev
```

## 🔗 Hosted Link
[Live Demo](https://ecommerce-two-jade.vercel.app/)



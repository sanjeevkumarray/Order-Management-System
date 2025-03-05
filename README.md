# E-Commerce Application

## Overview
This is a comprehensive E-Commerce platform designed for a seamless shopping experience. It includes features such as product management, user authentication, a coupon system, cart and wishlist management, order tracking, and more. The application is built using **Node.js, Express, and MongoDB** as the backend stack.

## Features
### User Management
- User Registration, Login, Logout
- Forgot Password, OTP Verification, and Password Reset
- Admin and User Role Authentication

### Product Management
- Add, Update, Delete, and Fetch Products
- Wishlist Functionality

### Coupon System
- Create, Update, and Apply Coupons

### Shopping Cart Management
- Add/Remove Products from Cart
- Increment/Decrement Product Quantity

### Order Management
- Create Orders, Track Orders, and View All Orders (Admin)
- Update Order Status

### FAQ and About Us Section
- Manage FAQs and About Us information dynamically

---

## API Endpoints
### Authentication Routes (`/api/user`)
- `POST /register` – Register a new user
- `POST /login` – Login user
- `POST /logout` – Logout user
- `GET /loggedIn` – Check if user is logged in
- `GET /adminLoggedIn` – Check if admin is logged in
- `POST /forgetPassword` – Forgot password flow
- `POST /verifyOtp` – Verify OTP for password reset
- `POST /changePassword` – Change password
- `GET /` – Get all users (Admin only)
- `DELETE /:userId` – Delete a user by ID (Admin only)

### Product Routes (`/api/product`)
- `POST /` – Add a new product (Admin only)
- `GET /getproduct` – Get all products
- `GET /:id` – Get a single product by ID
- `DELETE /deleteproduct/:id` – Delete a product by ID (Admin only)
- `PUT /updateproduct/:id` – Update product details (Admin only)
- `POST /addToWishList/:productId` – Add product to wishlist

### Cart Routes (`/api/cart`)
- `POST /addSingleProduct` – Add a product to the cart
- `DELETE /removeSingleProduct/:productId` – Remove a product from the cart
- `GET /wishlist` – Get user’s wishlist
- `POST /addToWishlist` – Add to wishlist
- `DELETE /removeFromWishlist/:productId` – Remove from wishlist
- `POST /decrement` – Decrease product quantity in cart
- `POST /increment` – Increase product quantity in cart
- `GET /` – Get user’s cart

### Order Routes (`/api/orders`)
- `POST /createorder` – Create a new order
- `GET /myorders` – Get orders of the logged-in user
- `GET /all` – Get all orders (Admin only)
- `PATCH /:id` – Update order status (Admin only)

---

## Project Setup
### Prerequisites
- **Node.js** (v14+)
- **MongoDB** (Atlas or Local)

### Installation
```sh
# Clone the repository
git clone <repository-url>
cd e-commerce

# Install dependencies
npm install

# Start backend server
cd backend
node index.js

# Start frontend server
cd frontend
npm run dev
```

### Hosted Link
[Live Demo](https://ecommerce-two-jade.vercel.app/)

---

# Order Processing System

## Objective
Develop a **scalable, event-driven Order Processing System** using **Node.js, Express, MongoDB, Redis, and AWS**. The system should allow users to place orders, process them asynchronously, and send notifications upon completion.

## Scope of Work
### 1. User Authentication (JWT & Refresh Tokens)
- **JWT-based authentication** with access and refresh tokens.
- API Endpoints:
  - `POST /api/auth/register` – Register a new user
  - `POST /api/auth/login` – User login
  - `POST /api/auth/refresh` – Refresh authentication token

### 2. Order Management
- Order Structure:
  - `orderId` (Unique Identifier)
  - `userId` (Who placed the order)
  - `items` (Array of products ordered)
  - `totalAmount`
  - `status` (Pending, Processed, Failed)
- API Endpoints:
  - `POST /api/orders` – Create an order
  - `GET /api/orders/:id` – Fetch order details

### 3. Inventory Check (Stock Validation)
- Validate product availability before order confirmation.
- Reject orders if items are out of stock.
- Use an **Inventory Service** (MongoDB Collection) to track stock levels.

### 4. Asynchronous Processing with AWS SQS
- Orders are **pushed to an AWS SQS queue** after validation.
- **Order Processor Worker**:
  - Reads from AWS SQS.
  - Updates order status (Processed/Failed).

### 5. Caching with Redis
- Cache order details for quick retrieval.
- **Set expiration (e.g., 10 minutes)** to avoid stale data.
- If an order is not found in Redis, fetch from MongoDB and update cache.

### 6. Email Notifications with AWS SES
- Send order confirmation emails after processing.
- Email includes:
  - Order ID
  - List of purchased items
  - Order status (Processed/Failed)
- Use **AWS SES** for email delivery.

---

## Technical Stack
### Backend Technologies
- **Node.js + Express.js** for API development
- **MongoDB** for database storage
- **Redis** for caching
- **JWT-based authentication**
- **AWS SQS** for async order processing
- **AWS SES** for order confirmation emails
- **Proper error handling and retry mechanisms**

## System Architecture
1. **Client/User**
   - Places an order via API.
   - Receives confirmation email.
2. **Order Service (Express.js + MongoDB)**
   - Handles order creation.
   - Validates inventory.
   - Pushes order to **AWS SQS**.
3. **Order Processor Worker (Node.js Service)**
   - Reads from **AWS SQS**.
   - Updates order status.
   - Caches order in **Redis**.
   - Sends email notifications via **AWS SES**.
4. **AWS Services**
   - **SQS**: Manages async processing queue.
   - **SES**: Sends email notifications.

---

## Expected Deliverables
1. **GitHub Repository**
   - Well-structured codebase
   - Proper **README** with setup instructions
2. **Postman Collection** for API Testing
3. **Short Explanation** (Optional)
   - Brief document or video explaining system architecture & approach

## Evaluation Criteria
✅ Backend Concepts (Auth, Async Processing, Caching)  
✅ AWS Integration (SQS, SES, Redis Optimization)  
✅ Code Quality (Structure, Modularity, Documentation)  
✅ Error Handling & Resilience (Retries, Stock Validation)  


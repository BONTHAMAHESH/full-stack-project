# SB Foods Backend API

A comprehensive Node.js backend for the SB Foods premium food ordering platform, built with Express.js and MongoDB.

## 🚀 Features

- **User Authentication & Authorization** - JWT-based auth with role-based access control
- **Menu Management** - Complete CRUD operations for dishes and categories
- **Order Processing** - Full order lifecycle management with real-time status updates
- **Shopping Cart** - Persistent cart functionality with item customizations
- **Review System** - Customer reviews and ratings with helpful voting
- **User Profiles** - Address management, preferences, and order history
- **Search & Filtering** - Advanced dish search with multiple filter options
- **Late Night Ordering** - Special midnight menu support
- **Admin Dashboard** - Complete admin functionality for managing the platform

## 🛠️ Tech Stack

- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JWT (JSON Web Tokens)
- **Security**: Helmet, CORS, Rate Limiting
- **Validation**: Express Validator
- **File Upload**: Multer
- **Environment**: dotenv

## 📁 Project Structure

```
├── controllers/          # Route controllers
├── middleware/          # Custom middleware
├── models/             # Mongoose models
├── routes/             # API routes
├── scripts/            # Utility scripts
├── uploads/            # File uploads directory
├── .env.example        # Environment variables template
├── server.js           # Main server file
└── package.json        # Dependencies and scripts
```

## 🚦 Getting Started

### Prerequisites

- Node.js (v16 or higher)
- MongoDB (local or cloud instance)
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd sb-foods-backend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   ```
   
   Edit `.env` with your configuration:
   ```env
   PORT=5000
   NODE_ENV=development
   MONGODB_URI=mongodb://localhost:27017/sb-foods
   JWT_SECRET=your-super-secret-jwt-key-here
   JWT_EXPIRE=7d
   ```

4. **Start MongoDB**
   Make sure MongoDB is running on your system

5. **Seed the database** (optional)
   ```bash
   npm run seed
   ```

6. **Start the server**
   ```bash
   # Development mode with auto-restart
   npm run dev
   
   # Production mode
   npm start
   ```

The API will be available at `http://localhost:5000`

## 📚 API Documentation

### Authentication Endpoints

| Method | Endpoint | Description | Access |
|--------|----------|-------------|---------|
| POST | `/api/auth/register` | Register new user | Public |
| POST | `/api/auth/login` | User login | Public |
| GET | `/api/auth/me` | Get current user | Private |
| PUT | `/api/auth/profile` | Update profile | Private |
| PUT | `/api/auth/change-password` | Change password | Private |

### Dish Endpoints

| Method | Endpoint | Description | Access |
|--------|----------|-------------|---------|
| GET | `/api/dishes` | Get all dishes | Public |
| GET | `/api/dishes/:id` | Get single dish | Public |
| GET | `/api/dishes/popular` | Get popular dishes | Public |
| GET | `/api/dishes/featured` | Get featured dishes | Public |
| GET | `/api/dishes/late-night` | Get late night dishes | Public |
| POST | `/api/dishes` | Create dish | Admin/Restaurant |
| PUT | `/api/dishes/:id` | Update dish | Admin/Restaurant |
| DELETE | `/api/dishes/:id` | Delete dish | Admin/Restaurant |

### Order Endpoints

| Method | Endpoint | Description | Access |
|--------|----------|-------------|---------|
| POST | `/api/orders` | Create order | Private |
| GET | `/api/orders` | Get user orders | Private |
| GET | `/api/orders/:id` | Get single order | Private |
| PUT | `/api/orders/:id/cancel` | Cancel order | Private |
| PUT | `/api/orders/:id/rate` | Rate order | Private |
| PUT | `/api/orders/:id/status` | Update order status | Admin/Restaurant |

### Cart Endpoints

| Method | Endpoint | Description | Access |
|--------|----------|-------------|---------|
| GET | `/api/cart` | Get user cart | Private |
| POST | `/api/cart/add` | Add item to cart | Private |
| PUT | `/api/cart/item/:itemId` | Update cart item | Private |
| DELETE | `/api/cart/item/:itemId` | Remove from cart | Private |
| DELETE | `/api/cart/clear` | Clear cart | Private |

### Category Endpoints

| Method | Endpoint | Description | Access |
|--------|----------|-------------|---------|
| GET | `/api/categories` | Get all categories | Public |
| GET | `/api/categories/:slug` | Get category with dishes | Public |
| POST | `/api/categories` | Create category | Admin |
| PUT | `/api/categories/:id` | Update category | Admin |
| DELETE | `/api/categories/:id` | Delete category | Admin |

## 🔐 Authentication

The API uses JWT (JSON Web Tokens) for authentication. Include the token in the Authorization header:

```
Authorization: Bearer <your-jwt-token>
```

### User Roles

- **user**: Regular customers (default)
- **restaurant**: Restaurant owners/managers
- **admin**: Platform administrators

## 📊 Database Models

### User Model
- Personal information (name, email, phone)
- Authentication (password, role)
- Addresses and preferences
- Order history and favorites

### Dish Model
- Basic info (name, description, price)
- Media (images, videos)
- Categorization and tags
- Availability and timing
- Ratings and reviews
- Customization options

### Order Model
- Order items and quantities
- Pricing breakdown
- Delivery information
- Status tracking
- Payment details
- Timeline and ratings

### Category Model
- Category information
- Visual elements (icon, image)
- Dish count tracking

### Review Model
- User ratings and comments
- Order verification
- Helpful voting system

## 🛡️ Security Features

- **Helmet**: Security headers
- **CORS**: Cross-origin resource sharing
- **Rate Limiting**: API request limiting
- **Input Validation**: Request data validation
- **Password Hashing**: bcrypt for secure passwords
- **JWT Authentication**: Secure token-based auth

## 🚀 Deployment

### Environment Variables for Production

```env
NODE_ENV=production
PORT=5000
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/sb-foods
JWT_SECRET=your-production-jwt-secret
```

### Docker Deployment (Optional)

```dockerfile
FROM node:16-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
EXPOSE 5000
CMD ["npm", "start"]
```

## 📈 Performance Optimizations

- **Database Indexing**: Optimized queries with proper indexes
- **Compression**: Gzip compression for responses
- **Caching**: Strategic caching for frequently accessed data
- **Pagination**: Efficient data pagination
- **Lean Queries**: Optimized MongoDB queries

## 🧪 Testing

```bash
# Run tests (when implemented)
npm test

# Run tests with coverage
npm run test:coverage
```

## 📝 API Response Format

### Success Response
```json
{
  "success": true,
  "data": { ... },
  "count": 10,
  "pagination": {
    "page": 1,
    "limit": 10,
    "pages": 5
  }
}
```

### Error Response
```json
{
  "success": false,
  "message": "Error description",
  "errors": [ ... ]
}
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📄 License

This project is licensed under the MIT License.

## 🆘 Support

For support and questions:
- Email: support@sbfoods.com
- Documentation: [API Docs](https://api.sbfoods.com/docs)
- Issues: [GitHub Issues](https://github.com/sbfoods/backend/issues)

---

Built with ❤️ by the SB Foods Team
# 🚗 Ride Sharing Microservices Platform

A comprehensive ride-sharing platform built with microservices architecture, featuring user management, captain (driver) services, ride booking, and API gateway integration.

## 🌟 Features

- **Microservices Architecture**: Scalable and modular design with independent services
- **User Management**: Complete user authentication and profile management
- **Captain Services**: Driver registration, authentication, and profile management
- **Ride Management**: Ride booking, tracking, and completion system
- **API Gateway**: Centralized routing and load balancing
- **Message Queue Integration**: RabbitMQ for inter-service communication
- **Authentication & Authorization**: JWT-based secure authentication
- **Token Blacklisting**: Enhanced security with token invalidation
- **Database Integration**: MongoDB for data persistence

## 🏗️ Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   User Service  │    │ Captain Service │    │  Ride Service   │
│                 │    │                 │    │                 │
│ • Authentication│    │ • Driver Auth   │    │ • Ride Booking  │
│ • User Profile  │    │ • Profile Mgmt  │    │ • Ride Tracking │
│ • Token Mgmt    │    │ • Token Mgmt    │    │ • Ride History  │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
                    ┌─────────────────┐
                    │  API Gateway    │
                    │                 │
                    │ • Request Router│
                    │ • Load Balancer │
                    │ • Rate Limiting │
                    └─────────────────┘
                                 │
                    ┌─────────────────┐
                    │   RabbitMQ      │
                    │                 │
                    │ • Message Queue │
                    │ • Event Handling│
                    │ • Service Comm  │
                    └─────────────────┘
```

## 📁 Project Structure

```
Ride-Sharing-Microservices/
├── captain/                    # Captain (Driver) Service
│   ├── controllers/           # Business logic controllers
│   ├── models/               # Database models
│   ├── routes/               # API routes
│   ├── middleware/           # Authentication middleware
│   ├── service/              # RabbitMQ service
│   └── db/                   # Database connection
├── gateway/                   # API Gateway Service
│   └── app.js                # Gateway routing logic
├── ride/                      # Ride Management Service
│   ├── controller/           # Ride business logic
│   ├── models/               # Ride data models
│   ├── routes/               # Ride API endpoints
│   ├── middleware/           # Request validation
│   ├── service/              # Message queue service
│   └── db/                   # Database connection
└── user/                      # User Management Service
    ├── controllers/          # User controllers
    ├── models/               # User & token models
    ├── routes/               # User API routes
    ├── middleware/           # Auth middleware
    ├── service/              # RabbitMQ integration
    └── db/                   # Database connection
```

## 🚀 Getting Started

### Prerequisites

- Node.js (v14+)
- MongoDB
- RabbitMQ
- npm or yarn

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/HarshManiar1804/Ride-Sharing-Microservices.git
   cd Ride-Sharing-Microservices
   ```

2. **Install dependencies for each service**

   ```bash
   # User Service
   cd user && npm install

   # Captain Service
   cd ../captain && npm install

   # Ride Service
   cd ../ride && npm install

   # Gateway Service
   cd ../gateway && npm install
   ```

3. **Set up environment variables**
   Create `.env` files in each service directory with:

   ```env
   PORT=3000
   MONGODB_URI=mongodb://localhost:27017/rideshare
   JWT_SECRET=your-jwt-secret
   RABBITMQ_URL=amqp://localhost
   ```

4. **Start the services**
   ```bash
   # Start each service in separate terminals
   cd user && npm start
   cd captain && npm start
   cd ride && npm start
   cd gateway && npm start
   ```

## 🔌 API Endpoints

### User Service (Port: 3001)

- `POST /api/users/register` - User registration
- `POST /api/users/login` - User authentication
- `POST /api/users/logout` - User logout
- `GET /api/users/profile` - Get user profile

### Captain Service (Port: 3002)

- `POST /api/captains/register` - Captain registration
- `POST /api/captains/login` - Captain authentication
- `POST /api/captains/logout` - Captain logout
- `GET /api/captains/profile` - Get captain profile

### Ride Service (Port: 3003)

- `POST /api/rides/book` - Book a new ride
- `GET /api/rides/history` - Get ride history
- `PUT /api/rides/:id/status` - Update ride status
- `GET /api/rides/:id` - Get ride details

### Gateway (Port: 3000)

- All requests are routed through the gateway
- Load balancing and request distribution
- Rate limiting and authentication

## 🛠️ Technologies Used

- **Backend**: Node.js, Express.js
- **Database**: MongoDB, Mongoose
- **Message Queue**: RabbitMQ
- **Authentication**: JWT (JSON Web Tokens)
- **Architecture**: Microservices
- **API Gateway**: Custom Express.js gateway

## 🔒 Security Features

- JWT-based authentication
- Token blacklisting for secure logout
- Password hashing with bcrypt
- Route protection middleware
- Input validation and sanitization

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 👨‍💻 Author

**Harsh Maniar**

- GitHub: [@HarshManiar1804](https://github.com/HarshManiar1804)
- LinkedIn: [harshmaniar210](https://www.linkedin.com/in/harshmaniar210/)

## 🙏 Acknowledgments

- Express.js community for excellent documentation
- MongoDB team for the robust database solution
- RabbitMQ for reliable message queuing
- Open source community for inspiration and support

---

⭐ **If you found this project helpful, please give it a star!** ⭐
